
.. _program_listing_file_ngind_kernel_render_program.cc:

Program Listing for File program.cc
===================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_program.cc>` (``ngind/kernel/render/program.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "program.h"
   
   #include "resources/resources_manager.h"
   
   namespace ngind {
   
   Program::Program(const std::string& program_name) {
       auto* vertex = ResourcesManager::getInstance()->load<ShaderResource>(program_name + ".vs");
       auto* fragment = ResourcesManager::getInstance()->load<ShaderResource>(program_name + ".fs");
   
       this->_program = glCreateProgram();
       glAttachShader(this->_program, vertex->getShader());
       glAttachShader(this->_program, fragment->getShader());
       glLinkProgram(this->_program);
   
       GLint success;
       glGetProgramiv(this->_program, GL_LINK_STATUS, &success);
       if (!success) {
       }
   
       ResourcesManager::getInstance()->release(vertex->getResourcePath());
       ResourcesManager::getInstance()->release(fragment->getResourcePath());
   }
   
   Program::~Program() {
       glDeleteProgram(this->_program);
   }
   
   } // namespace ngind
