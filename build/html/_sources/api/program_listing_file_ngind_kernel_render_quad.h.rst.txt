
.. _program_listing_file_ngind_kernel_render_quad.h:

Program Listing for File quad.h
===============================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_quad.h>` (``ngind/kernel/render/quad.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #ifndef NGIND_QUAD_H
   #define NGIND_QUAD_H
   
   #include "GL/glew.h"
   
   #include <initializer_list>
   #include <cstdio>
   
   namespace ngind {
   
   class Quad {
   public:
       Quad(std::initializer_list<GLfloat>, const size_t&);
   
       ~Quad();
   
       Quad(const Quad&) = delete;
       Quad& operator= (const Quad&) = delete;
   
       inline GLuint getVAO() const {
           return _vao;
       }
   
   private:
       GLuint _vao;
   
       GLuint _vbo;
   
       GLuint _ebo;
   };
   
   } // namespace ngind
   
   #endif //NGIND_QUAD_H
