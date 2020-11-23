
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_program.h:

Program Listing for File program.h
==================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_program.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/program.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #ifndef NGIND_PROGRAM_H
   #define NGIND_PROGRAM_H
   
   #include <string>
   
   #include "resources/shader_resource.h"
   #include "glm/glm.hpp"
   #include "glm/gtc/type_ptr.hpp"
   
   namespace ngind {
   
   class Program {
   public:
       explicit Program(const std::string&);
   
       ~Program();
   
       Program(const Program&) = delete;
       Program& operator= (const Program&) = delete;
   
       inline void use() const {
           glUseProgram(this->_program);
       }
   
       inline void setVector4(const std::string& name, const glm::vec4& v) {
           glUniform4f(glGetUniformLocation(this->_program, name.c_str()), v.x, v.y, v.z, v.w);
       }
   
       inline void setMatrix4(const std::string& name, const glm::mat4& m) {
           glUniformMatrix4fv(glGetUniformLocation(this->_program, name.c_str()), 1, GL_FALSE, glm::value_ptr(m));
       }
   
       inline void setInteger(const std::string& name, const int& i) {
           glUniform1i(glGetUniformLocation(this->_program, name.c_str()), i);
       }
   private:
       GLuint _program;
   };
   
   } // namespace ngind
   
   #endif //NGIND_PROGRAM_H
