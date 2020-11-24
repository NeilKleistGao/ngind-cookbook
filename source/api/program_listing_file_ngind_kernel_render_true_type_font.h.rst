
.. _program_listing_file_ngind_kernel_render_true_type_font.h:

Program Listing for File true_type_font.h
=========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_true_type_font.h>` (``ngind/kernel/render/true_type_font.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_TRUE_TYPE_FONT_H
   #define NGIND_TRUE_TYPE_FONT_H
   
   #include <string>
   
   #include <freetype2/ft2build.h>
   #include FT_FREETYPE_H
   
   namespace ngind {
   
   class TrueTypeFont {
   public:
       TrueTypeFont();
   
       ~TrueTypeFont();
   
       inline void setFontFace(FT_Face face) {
           _font_face = face;
       }
   private:
       FT_Face _font_face;
   };
   
   } // namespace ngind
   
   #endif //NGIND_TRUE_TYPE_FONT_H
