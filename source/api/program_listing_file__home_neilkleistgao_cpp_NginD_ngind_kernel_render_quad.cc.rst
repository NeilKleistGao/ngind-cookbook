
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_quad.cc:

Program Listing for File quad.cc
================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_quad.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/quad.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "quad.h"
   
   namespace ngind {
   
   Quad::Quad(std::initializer_list<GLfloat> vs, const size_t& color_size) {
       if (vs.size() == 0) {
           // TODO: error detected
       }
   
       size_t size = vs.size();
       auto* vertex = new GLfloat[size];
       auto it = vs.begin();
       for (int i = 0; i < size; i++, it++) {
           vertex[i] = *it;
       }
   
       constexpr GLuint indices[] = {
               0, 1, 3,
               1, 2, 3
       };
   
       glGenVertexArrays(1, &_vao);
       glGenBuffers(1, &_vbo);
       glGenBuffers(1, &_ebo);
   
       glBindVertexArray(_vao);
   
       glBindBuffer(GL_ARRAY_BUFFER, _vbo);
       glBufferData(GL_ARRAY_BUFFER, sizeof(GLfloat) * size, vertex, GL_STATIC_DRAW);
   
       glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, _ebo);
       glBufferData(GL_ELEMENT_ARRAY_BUFFER, sizeof(indices), indices, GL_STATIC_DRAW);
   
       // TODO: dynamic size
       glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 8 * sizeof(GLfloat), reinterpret_cast<GLvoid*>(0));
       glEnableVertexAttribArray(0);
       glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, 8 * sizeof(GLfloat), reinterpret_cast<GLvoid*>(3 * sizeof(GLfloat)));
       glEnableVertexAttribArray(1);
       glVertexAttribPointer(2, 2, GL_FLOAT, GL_FALSE, 8 * sizeof(GLfloat), reinterpret_cast<GLvoid*>(6 * sizeof(GLfloat)));
       glEnableVertexAttribArray(2);
   
       glBindVertexArray(0);
   }
   
   Quad::~Quad() {
       glDeleteVertexArrays(1, &_vao);
       glDeleteBuffers(1, &_vbo);
       glDeleteBuffers(1, &_ebo);
   }
   
   } // namespace ngind
