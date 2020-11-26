
.. _program_listing_file_ngind_kernel_objects_object.h:

Program Listing for File object.h
=================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_objects_object.h>` (``ngind/kernel/objects/object.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_OBJECT_H
   #define NGIND_OBJECT_H
   
   #include <map>
   #include <iostream>
   
   #include "kernel/utils/serialization.h"
   #include "memory/auto_collection_object.h"
   #include "updatable_object.h"
   #include "components/component.h"
   
   namespace ngind {
   
   class Object : public Serializable, public AutoCollectionObject, public UpdatableObject {
   public:
       Object();
   
       ~Object() override;
   
       void serialize(std::ostream&) const override;
   
       void deserialize(std::istream&) override;
   
       void addChild(const std::string&, Object*);
   
       void removeChild(const std::string&);
   
       Object* getChildByName(const std::string&);
   
       inline void setParent(Object* object) {
           this->_parent = object;
       }
   
       inline Object* getParent() {
           return this->_parent;
       }
   
       virtual void update(const float&);
   
       virtual inline void addComponent(const std::string& name, Component* component) {
           if (_components.find(name) == _components.end()) {
               _components[name] = component;
               component->setParent(this);
           }
       }
   
       template<typename Type, typename std::enable_if_t<std::is_base_of_v<Component, Type>> N = 0>
       Type* getComponent(const std::string& name) {
           if (_components.find(name) == _components.end()) {
               return nullptr;
           }
   
           return static_cast<Type>(_components[name]);
       }
   
       template<typename Type, typename std::enable_if_t<std::is_base_of_v<Component, Type>> N = 0>
       void removeComponent(const std::string& name) {
           if (_components.find(name) == _components.end()) {
               return;
           }
   
           auto p = static_cast<Type>(_components[name]);
           delete p;
           p = _components[name] = nullptr;
           _components.erase(name);
       }
   
   protected:
       std::map<std::string, Object*> _children;
   
       std::map<std::string, Component*> _components;
   
       Object* _parent;
   };
   } // namespace ngind
   
   
   
   #endif //NGIND_OBJECT_H
