
.. _program_listing_file_ngind_kernel_resources_texture_resource.h:

Program Listing for File texture_resource.h
===========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_texture_resource.h>` (``ngind/kernel/resources/texture_resource.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: texture_resource.h
   // LAST MODIFY: 2020/11/1
   
   #ifndef NGIND_TEXTURE_RESOURCE_H
   #define NGIND_TEXTURE_RESOURCE_H
   
   #include <iostream>
   
   #include "render/texture.h"
   #include "resource.h"
   #include "render/png_image.h"
   #include "math/vector.h"
   
   namespace ngind {
   
   class TextureResource : public Resource {
   public:
       const static std::string IMAGE_RESOURCE_PATH;
   
       TextureResource() = default;
       ~TextureResource() override = default;
       virtual void load(const std::string&);
   
       inline GLuint getTextureID() const {
           return _texture->getTextureID();
       }
   
       inline Vector2D getTextureSize() const {
           return _texture->getSize();
       }
   
       inline float getTextureWidth() const {
           return _texture->getWidth();
       }
   
       inline float getTextureHeight() const {
           return _texture->getHeight();
       }
   
       inline TextureColorMode getTextureColorMode() const {
           return _texture->getColorMode();
       }
   
   private:
       Texture* _texture;
   };
   
   }
   
   #endif //NGIND_TEXTURE_RESOURCE_H
