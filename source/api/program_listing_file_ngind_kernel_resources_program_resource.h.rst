
.. _program_listing_file_ngind_kernel_resources_program_resource.h:

Program Listing for File program_resource.h
===========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_program_resource.h>` (``ngind/kernel/resources/program_resource.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: program_resource.h
   // LAST MODIFY: 2020/11/1
   
   #ifndef NGIND_PROGRAM_RESOURCE_H
   #define NGIND_PROGRAM_RESOURCE_H
   
   #include "resource.h"
   #include "render/program.h"
   
   namespace ngind {
   
   class ProgramResource : public Resource {
   public:
       ProgramResource();
       ~ProgramResource();
   
       void load(const std::string&) override;
   
       inline Program* getProgram() const {
           return _program;
       }
   private:
       Program* _program;
   };
   
   } // namespace ngind
   
   #endif //NGIND_PROGRAM_RESOURCE_H
