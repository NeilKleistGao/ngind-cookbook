
.. _program_listing_file_ngind_kernel_resources_font_resource.h:

Program Listing for File font_resource.h
========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_font_resource.h>` (``ngind/kernel/resources/font_resource.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: font_resource.h
   // LAST MODIFY: 2020/10/19
   
   #ifndef NGIND_FONT_RESOURCE_H
   #define NGIND_FONT_RESOURCE_H
   
   #include "resource.h"
   #include "render/true_type_font.h"
   
   namespace ngind {
   
   class FontResource : public Resource {
   public:
       const static std::string FONT_RESOURCE_PATH;
   
       FontResource();
       ~FontResource() override;
   
       void load(const std::string&) override;
   private:
       TrueTypeFont* _font;
   };
   
   } // namespace ngind
   
   #endif //NGIND_FONT_RESOURCE_H
