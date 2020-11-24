
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_font_factory.cc:

Program Listing for File font_factory.cc
========================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_font_factory.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/font_factory.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "font_factory.h"
   
   namespace ngind {
   FontFactory* FontFactory::_instance = nullptr;
   
   FontFactory::FontFactory() : _library(nullptr) {
       auto error = FT_Init_FreeType(&_library);
       if (error) {
           // TODO: throw
       }
   }
   
   FontFactory* FontFactory::getInstance() {
       if (_instance == nullptr) {
           _instance = new(std::nothrow) FontFactory();
       }
   
       return _instance;
   }
   
   void FontFactory::destroyInstance() {
       if (_instance != nullptr) {
           delete _instance;
           _instance = nullptr;
       }
   }
   
   FT_Face FontFactory::loadFontFace(const std::string& filename, const long& index) {
       FT_Face face = nullptr;
       auto error = FT_New_Face(_library, filename.c_str(), index, &face);
       if (error) {
           face = nullptr;
       }
   
       return face;
   }
   
   }
