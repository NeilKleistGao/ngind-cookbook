
.. _program_listing_file_ngind_kernel_filesystem_output_stream.cc:

Program Listing for File output_stream.cc
=========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_filesystem_output_stream.cc>` (``ngind/kernel/filesystem/output_stream.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "output_stream.h"
   
   namespace ngind {
   const std::string OutputStream::STDOUT = "__STDOUT__";
   const std::string OutputStream::STDERR = "__STDERR__";
   
   OutputStream::OutputStream(std::string filename) : _filename(std::move(filename)) {
       if (_filename != STDOUT && _filename != STDERR) {
           _stream.open(filename);
       }
   }
   
   OutputStream::~OutputStream() {
       this->close();
   }
   } // namespace ngind
