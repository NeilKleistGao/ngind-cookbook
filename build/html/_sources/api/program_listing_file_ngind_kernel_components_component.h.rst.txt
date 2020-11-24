
.. _program_listing_file_ngind_kernel_components_component.h:

Program Listing for File component.h
====================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_components_component.h>` (``ngind/kernel/components/component.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_COMPONENT_H
   #define NGIND_COMPONENT_H
   
   #include <string>
   
   #include "objects/updatable_object.h"
   #include "resources/config_resource.h"
   
   namespace ngind {
   
   class Object;
   
   class Component : public UpdatableObject {
   public:
       Component() = default;
       virtual ~Component() = default;
       Component(const Component&) = delete;
       Component& operator= (const Component&) = delete;
   
       virtual void update(const float&) {}
   
       virtual void init(const typename ConfigResource::JsonObject& object) {}
   
       inline Object* getParent() const {
           return _parent;
       }
   
       inline void setParent(Object* parent) {
           _parent = parent;
       }
   
   protected:
       Object* _parent;
   };
   
   } // namespace ngind
   
   #endif //NGIND_COMPONENT_H
