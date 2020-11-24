
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_objects_object.cc:

Program Listing for File object.cc
==================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_objects_object.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/objects/object.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "object.h"
   
   namespace ngind {
   
   Object::Object() : AutoCollectionObject(), _parent(nullptr) {
       this->_children.clear();
       this->_components.clear();
   }
   
   Object::~Object() {
       for (auto it : this->_children) {
           it.second->removeReference();
   
           if (it.second->getSustain() == 0) {
               delete it.second;
               it.second = nullptr;
           }
       }
   
       for (auto it : this->_components) {
           delete it.second;
           it.second = nullptr;
       }
   
       this->_children.clear();
       this->_components.clear();
   }
   
   void Object::serialize(std::ostream& stream) const {
   }
   
   void Object::deserialize(std::istream& stream) {
   }
   
   void Object::addChild(const std::string& name, Object* object) {
       auto it = this->_children.find(name);
       if (it == this->_children.end()) {
           this->_children[name] = object;
           object->addReference();
           object->setParent(this);
       }
   }
   
   void Object::removeChild(const std::string& name) {
       auto it = this->_children.find(name);
       Object* object = nullptr;
       if (it != this->_children.end()) {
           object = it->second;
           this->_children.erase(it);
       }
   
       if (object != nullptr) {
           object->removeReference();
           object->setParent(nullptr);
           if (object->getSustain() == 0) {
               delete object;
               object = nullptr;
           }
       }
   }
   
   Object* Object::getChildByName(const std::string& name) {
       Object* object = nullptr;
       auto it = this->_children.find(name);
       if (it != this->_children.end()) {
           object = it->second;
       }
   
       return object;
   }
   
   void Object::update(const float& delta) {
       for (auto child : this->_children) {
           child.second->update(delta);
       }
   
       for (auto component : this->_components) {
           component.second->update(delta);
       }
   }
   
   } // namespace ngind
