
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_filesystem_output_stream.h:

Program Listing for File output_stream.h
========================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_filesystem_output_stream.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/filesystem/output_stream.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_OUTPUT_STREAM_H
   #define NGIND_OUTPUT_STREAM_H
   
   #include <iostream>
   #include <fstream>
   
   namespace ngind {
   
   class OutputStream {
   public:
       const static std::string STDOUT, STDERR;
   
       explicit OutputStream(std::string);
       ~OutputStream();
   
       OutputStream(const OutputStream&) = delete;
       OutputStream& operator= (const OutputStream&) = delete;
   
       template<typename Type>
       void output(const Type& content) {
           if (_filename == STDOUT) {
               std::cout << content;
           }
           else if (_filename == STDERR) {
               std::cerr << content;
           }
           else {
               _stream << content;
           }
       }
   
       inline void close() {
           if (_stream.is_open()) {
               _stream.close();
           }
       }
   
       inline bool isOpen() {
           return _stream.is_open();
       }
   private:
       std::ofstream _stream;
       std::string _filename;
   };
   
   template<typename Type>
   OutputStream& operator<< (OutputStream& stream, const Type& content) {
       stream.output(content);
       return stream;
   }
   
   } // namespace ngind
   
   #endif //NGIND_OUTPUT_STREAM_H
