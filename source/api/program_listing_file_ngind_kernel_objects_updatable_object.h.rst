
.. _program_listing_file_ngind_kernel_objects_updatable_object.h:

Program Listing for File updatable_object.h
===========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_objects_updatable_object.h>` (``ngind/kernel/objects/updatable_object.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_UPDATABLE_OBJECT_H
   #define NGIND_UPDATABLE_OBJECT_H
   
   namespace ngind {
   
   class UpdatableObject {
   public:
       virtual void update(const float&) = 0;
   };
   } // namespace ngind
   
   #endif //NGIND_UPDATABLE_OBJECT_H
