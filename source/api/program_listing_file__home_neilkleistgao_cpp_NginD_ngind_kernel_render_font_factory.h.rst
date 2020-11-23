
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_font_factory.h:

Program Listing for File font_factory.h
=======================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_font_factory.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/font_factory.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_FONT_FACTORY_H
   #define NGIND_FONT_FACTORY_H
   
   #include <string>
   
   #include "freetype2/ft2build.h"
   #include FT_FREETYPE_H
   
   namespace ngind {
   
   class FontFactory {
   public:
       static FontFactory* getInstance();
   
       static void destroyInstance();
   
       FT_Face loadFontFace(const std::string&, const long&);
   private:
       FontFactory();
   
       ~FontFactory() = default;
   
       static FontFactory* _instance;
   
       FT_Library _library;
   };
   
   } // namespace ngind
   
   #endif //NGIND_FONT_FACTORY_H
