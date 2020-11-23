
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_shader.h:

Program Listing for File shader.h
=================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_shader.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/shader.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: shader.h
   // LAST MODIFY: 2020/10/31
   
   #ifndef NGIND_SHADER_H
   #define NGIND_SHADER_H
   
   #include <string>
   
   #include "GL/glew.h"
   
   namespace ngind {
   
   class Shader {
   public:
       Shader(const std::string&, const int&);
       ~Shader();
       Shader(const Shader&) = delete;
       Shader& operator= (const Shader&) = delete;
   
       inline GLuint getShader() const {
           return _shader;
       }
   private:
       GLuint _shader;
   };
   
   } // namespace ngind
   
   #endif //NGIND_SHADER_H
