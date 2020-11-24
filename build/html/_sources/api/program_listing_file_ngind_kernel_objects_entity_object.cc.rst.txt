
.. _program_listing_file_ngind_kernel_objects_entity_object.cc:

Program Listing for File entity_object.cc
=========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_objects_entity_object.cc>` (``ngind/kernel/objects/entity_object.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "entity_object.h"
   
   namespace ngind {
   
   EntityObject::EntityObject() : Object(), _position(), _scale(), _rotation(0.0f), _z_order(0) {
   
   }
   
   void EntityObject::update(const float& delta) {
       Object::update(delta);
   }
   
   } // namespace ngind
