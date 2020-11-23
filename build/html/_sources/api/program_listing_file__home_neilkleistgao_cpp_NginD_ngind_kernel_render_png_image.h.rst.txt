
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_png_image.h:

Program Listing for File png_image.h
====================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_png_image.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/png_image.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // LAST MODIFY: 2020/11/1
   // FILENAME: png_image.h
   
   #ifndef NGIND_PNG_IMAGE_H
   #define NGIND_PNG_IMAGE_H
   
   #include <string>
   
   #include "glfw3.h"
   
   #include "rgba.h"
   #include "math/vector.h"
   
   namespace ngind {
   
   class PNGImage {
   public:
       const static std::string IMAGE_RESOURCE_PATH;
   
       PNGImage();
       explicit PNGImage(const std::string&);
       ~PNGImage();
   
       void loadPNG(const std::string& filename);
   
       inline GLFWimage *getImageData() {
           return _image;
       }
   
       inline Vector2D getImageSize() {
           return Vector2D{_image->width, _image->height};
       }
   
   private:
       GLFWimage *_image;
   };
   
   } // namespace ngind
   
   #endif //NGIND_PNG_IMAGE_H
