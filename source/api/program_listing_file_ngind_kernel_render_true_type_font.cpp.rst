
.. _program_listing_file_ngind_kernel_render_true_type_font.cpp:

Program Listing for File true_type_font.cpp
===========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_true_type_font.cpp>` (``ngind/kernel/render/true_type_font.cpp``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #include "true_type_font.h"
   
   namespace ngind {
   
   TrueTypeFont::TrueTypeFont() : _font_face(nullptr) {
   }
   
   TrueTypeFont::~TrueTypeFont() {
       auto error = FT_Done_Face(_font_face);
       if (error) {
       }
   }
   
   } // namespace ngind
