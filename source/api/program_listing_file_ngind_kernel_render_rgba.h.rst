
.. _program_listing_file_ngind_kernel_render_rgba.h:

Program Listing for File rgba.h
===============================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_rgba.h>` (``ngind/kernel/render/rgba.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: rgba.h
   // LAST MODIFY: 2020/10/25
   
   #ifndef NGIND_RGBA_H
   #define NGIND_RGBA_H
   
   #include "utils/converter.h"
   
   namespace ngind {
   
   struct RGBA {
       RGBA() = default;
       explicit RGBA(const std::string& code) {
           auto color = Converter::convertHexString(code.substr(1));
           r = (color & 0xFF000000) >> 24;
           g = (color & 0x00FF0000) >> 16;
           b = (color & 0x0000FF00) >> 8;
           a = color & 0x000000FF;
       }
   
       unsigned char r, g, b, a;
   };
   
   } // namespace ngind
   
   #endif //NGIND_RGBA_H
