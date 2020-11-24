
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_shader.cc:

Program Listing for File shader.cc
==================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_shader.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/shader.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: shader.cc
   // LAST MODIFY: 2020/10/31
   
   #include "shader.h"
   
   #include "filesystem/file.h"
   
   namespace ngind {
   
   Shader::Shader(const std::string& filename, const int& type) {
       File* fp = new File(filename, "r");
       std::string code = fp->readToEnd();
       fp->close();
   
       this->_shader = glCreateShader(type);
       const GLchar* str = code.c_str();
   
       glShaderSource(this->_shader, 1, &str, nullptr);
       glCompileShader(this->_shader);
   
       GLint success;
       glGetShaderiv(this->_shader, GL_COMPILE_STATUS, &success);
       if (!success) {
   
       }
   }
   
   Shader::~Shader() {
       glDeleteShader(this->_shader);
   }
   
   } // namespace ngind
