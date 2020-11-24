
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_resources_resources_manager.h:

Program Listing for File resources_manager.h
============================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_resources_resources_manager.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/resources/resources_manager.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: resources_manager.h
   // LAST MODIFY: 2020/10/11
   
   #ifndef NGIND_RESOURCES_MANAGER_H
   #define NGIND_RESOURCES_MANAGER_H
   
   #include <map>
   #include <functional>
   
   #include "resource.h"
   #include "coroutine/coroutine.h"
   
   namespace ngind {
   
   class ResourcesManager {
   public:
       static ResourcesManager* getInstance();
       static void destroyInstance();
   
       template<typename Type, typename std::enable_if_t<std::is_base_of_v<Resource, Type>, int> N = 0>
       Coroutine<Type*, std::string> preLoad(const std::string& path, std::function<void(Type*)> callback) {
           auto coroutine = Coroutine<Type*, std::string>(load, callback);
           coroutine.run(path);
           return coroutine;
       }
   
       template<typename Type, typename std::enable_if_t<std::is_base_of_v<Resource, Type>, int> N = 0>
       Type* load(const std::string& path) {
           if (this->_resources.find(path) != this->_resources.end()) {
               this->_resources[path]->addReference();
               return static_cast<Type*>(this->_resources[path]);
           }
   
           this->_resources[path] = new(std::nothrow) Type();
           if (this->_resources[path] == nullptr) {
               //TODO: Exception Detect
           }
           else {
               this->_resources[path]->load(path);
               this->_resources[path]->addReference();
           }
   
           return static_cast<Type*>(this->_resources[path]);
       }
   
       void release(const std::string&);
   
       ResourcesManager(const ResourcesManager&) = delete;
       ResourcesManager(ResourcesManager&&) = delete;
   private:
       ResourcesManager() = default;
       ~ResourcesManager() = default;
   
       static ResourcesManager* _instance;
       std::map<std::string, Resource*> _resources;
   };
   
   } // namespace ngind
   
   #endif //NGIND_RESOURCES_MANAGER_H
