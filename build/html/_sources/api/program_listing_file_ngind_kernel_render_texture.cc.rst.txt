
.. _program_listing_file_ngind_kernel_render_texture.cc:

Program Listing for File texture.cc
===================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_texture.cc>` (``ngind/kernel/render/texture.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #include "texture.h"
   
   #include <cassert>
   
   #include "SOIL2/SOIL2.h"
   
   namespace ngind {
   
   Texture::Texture(const std::string& filename, const TextureColorMode& mode) {
       glGenTextures(1, &_texture_id);
       glBindTexture(GL_TEXTURE_2D, _texture_id);
   
       glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
       glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
       glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
       glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
   
       int width, height;
       unsigned char* img = nullptr;
       if (mode == TextureColorMode::MODE_RGB) {
           img = SOIL_load_image(filename.c_str(), &width, &height, nullptr, SOIL_LOAD_RGB);
   
           glTexImage2D(GL_TEXTURE_2D, 0, GL_RGB, width,
                        height, 0, GL_RGB, GL_UNSIGNED_BYTE, img);
           glBindTexture(GL_TEXTURE_2D, 0);
       }
       else if (mode == TextureColorMode::MODE_RGBA) {
           img = SOIL_load_image(filename.c_str(), &width, &height, nullptr, SOIL_LOAD_RGBA);
   
           glTexImage2D(GL_TEXTURE_2D, 0, GL_RGBA, width,
                        height, 0, GL_RGBA, GL_UNSIGNED_BYTE, img);
           glBindTexture(GL_TEXTURE_2D, 0);
       }
   
       _size = Vector2D{width, height};
       SOIL_free_image_data(img);
       _mode = mode;
   
       glBindTexture(GL_TEXTURE_2D, 0);
   }
   
   Texture::~Texture() {
       glDeleteTextures(1, &_texture_id);
   }
   
   } // namespace
