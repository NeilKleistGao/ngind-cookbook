
.. _program_listing_file_ngind_kernel_resources_program_resource.cc:

Program Listing for File program_resource.cc
============================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_program_resource.cc>` (``ngind/kernel/resources/program_resource.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: program_resource.h
   // LAST MODIFY: 2020/11/1
   
   #include "program_resource.h"
   
   namespace ngind {
   ProgramResource::ProgramResource() : _program(nullptr) {
   }
   
   ProgramResource::~ProgramResource() {
       delete _program;
       _program = nullptr;
   }
   
   void ProgramResource::load(const std::string& name) {
       if (_program != nullptr) {
           delete _program;
           _program = nullptr;
       }
   
       _program = new Program(name);
       this->_path = "program" + name;
   }
   
   } // namespace ngind
