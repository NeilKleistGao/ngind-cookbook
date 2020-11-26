
.. _program_listing_file_ngind_kernel_resources_resource.h:

Program Listing for File resource.h
===================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_resource.h>` (``ngind/kernel/resources/resource.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: resource.h
   // LAST MODIFY: 2020/10/11
   
   #ifndef NGIND_RESOURCE_H
   #define NGIND_RESOURCE_H
   
   #include <iostream>
   
   #include "memory/auto_collection_object.h"
   
   namespace ngind {
   
   class Resource : public AutoCollectionObject {
   public:
       virtual ~Resource() = default;
       virtual void load(const std::string&) = 0;
   
       inline const std::string getResourcePath() const {
           return _path;
       }
   
   protected:
       std::string _path;
   };
   
   } // namespace ngind
   
   #endif //NGIND_RESOURCE_H
