
.. _program_listing_file_ngind_kernel_resources_shader_resource.h:

Program Listing for File shader_resource.h
==========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_shader_resource.h>` (``ngind/kernel/resources/shader_resource.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: shader_resource.h
   // LAST MODIFY: 2020/10/28
   
   #ifndef NGIND_SHADER_RESOURCE_H
   #define NGIND_SHADER_RESOURCE_H
   
   #include "resource.h"
   #include "render/shader.h"
   
   namespace ngind {
   
   class ShaderResource : public Resource {
   public:
       const static std::string SHADER_RESOURCE_PATH;
   
       ShaderResource() = default;
       ~ShaderResource() override;
   
       virtual void load(const std::string&);
   
       inline GLuint getShader() {
           return _shader->getShader();
       }
   private:
       Shader* _shader;
   };
   
   } // namespace ngind
   
   #endif //NGIND_SHADER_RESOURCE_H
