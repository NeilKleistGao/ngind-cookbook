
.. _program_listing_file_ngind_kernel_resources_texture_resource.cc:

Program Listing for File texture_resource.cc
============================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_texture_resource.cc>` (``ngind/kernel/resources/texture_resource.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: texture_resource.cc
   // LAST MODIFY: 2020/11/1
   
   #include "texture_resource.h"
   
   namespace ngind {
   const std::string TextureResource::IMAGE_RESOURCE_PATH = "resources/images";
   
   void TextureResource::load(const std::string& filename) {
       if (this->_texture != nullptr) {
           delete this->_texture;
           this->_texture = nullptr;
       }
   
       this->_path = filename;
   
       int pos = filename.find_last_of('.');
       std::string ext = filename.substr(pos + 1);
   
       if (ext == "png") {
           _texture = new Texture(IMAGE_RESOURCE_PATH + "/" + filename, TextureColorMode::MODE_RGBA);
       }
       else if (ext == "jpg") {
           _texture = new Texture(IMAGE_RESOURCE_PATH + "/" + filename, TextureColorMode::MODE_RGB);
       }
       else {
           // TODO: unsupported format
       }
   }
   } // namespace ngind
