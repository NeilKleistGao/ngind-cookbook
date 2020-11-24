
.. _program_listing_file_ngind_kernel_resources_font_resource.cc:

Program Listing for File font_resource.cc
=========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_font_resource.cc>` (``ngind/kernel/resources/font_resource.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: font_resource.h
   // LAST MODIFY: 2020/10/19
   
   #include "font_resource.h"
   
   #include "render/font_factory.h"
   
   namespace ngind {
   const std::string FontResource::FONT_RESOURCE_PATH = "resources/fonts";
   
   FontResource::FontResource() : _font(nullptr) {
       _font = new TrueTypeFont();
   }
   
   FontResource::~FontResource() {
       delete _font;
       _font = nullptr;
   }
   
   void FontResource::load(const std::string& filename) {
       if (_font != nullptr) {
           auto face = FontFactory::getInstance()->loadFontFace(filename, 0);
           _font->setFontFace(face);
       }
   }
   
   } // namespace ngind
