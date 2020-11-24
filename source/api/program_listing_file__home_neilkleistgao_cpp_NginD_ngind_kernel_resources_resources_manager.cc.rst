
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_resources_resources_manager.cc:

Program Listing for File resources_manager.cc
=============================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_resources_resources_manager.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/resources/resources_manager.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: resources_manager.cc
   // LAST MODIFY: 2020/10/11
   
   #include "resources_manager.h"
   
   namespace ngind {
   ResourcesManager* ResourcesManager::_instance = nullptr;
   
   ResourcesManager* ResourcesManager::getInstance() {
       if (_instance == nullptr) {
           _instance = new(std::nothrow) ResourcesManager();
       }
   
       return _instance;
   }
   
   void ResourcesManager::destroyInstance() {
       if (_instance != nullptr) {
           delete _instance;
           _instance = nullptr;
       }
   }
   
   void ResourcesManager::release(const std::string& path) {
       if (this->_resources.find(path) == this->_resources.end()) {
           return;
       }
   
       this->_resources[path]->removeReference();
       if (this->_resources[path]->getSustain() == 0) {
           delete this->_resources[path];
           this-_resources.erase(path);
       }
   }
   
   } // namespace ngind
