
.. _program_listing_file_ngind_kernel_resources_shader_resource.cc:

Program Listing for File shader_resource.cc
===========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_shader_resource.cc>` (``ngind/kernel/resources/shader_resource.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: shader_resource.h
   // LAST MODIFY: 2020/10/31
   
   #include "shader_resource.h"
   
   namespace ngind {
   
   const std::string ShaderResource::SHADER_RESOURCE_PATH = "resources/shaders";
   
   ShaderResource::~ShaderResource() {
       if (_shader != nullptr) {
           delete _shader;
           _shader = nullptr;
       }
   }
   
   void ShaderResource::load(const std::string& filename) {
       if (_shader != nullptr) {
           delete _shader;
           _shader = nullptr;
       }
   
       this->_path = filename;
       int pos = filename.find_last_of('.');
       if (filename.substr(pos + 1) == "vs") {
           _shader = new Shader(SHADER_RESOURCE_PATH + "/" + filename, GL_VERTEX_SHADER);
       }
       else {
           _shader = new Shader(SHADER_RESOURCE_PATH + "/" + filename, GL_FRAGMENT_SHADER);
       }
   }
   
   } // namespace
