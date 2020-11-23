
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_texture.h:

Program Listing for File texture.h
==================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_texture.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/texture.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_TEXTURE_H
   #define NGIND_TEXTURE_H
   
   #include <string>
   
   #include "GL/glew.h"
   #include "math/vector.h"
   
   namespace ngind {
   
   enum TextureColorMode {
       MODE_RGB = GL_RGB,
       MODE_RGBA = GL_RGBA
   };
   
   class Texture {
   public:
       Texture(const std::string&, const TextureColorMode&);
   
       ~Texture();
   
       Texture(const Texture&) = delete;
       Texture& operator= (const Texture&) = delete;
   
       inline GLuint getTextureID() const {
           return _texture_id;
       }
   
       inline float getWidth() const {
           return _size.getX();
       }
   
       inline float getHeight() const {
           return _size.getY();
       }
   
       inline Vector2D getSize() const {
           return _size;
       }
   
       inline TextureColorMode getColorMode() const {
           return _mode;
       }
   
   private:
       GLuint _texture_id;
   
       Vector2D _size;
   
       TextureColorMode _mode;
   };
   
   } // namespace ngind
   
   #endif //NGIND_TEXTURE_H
