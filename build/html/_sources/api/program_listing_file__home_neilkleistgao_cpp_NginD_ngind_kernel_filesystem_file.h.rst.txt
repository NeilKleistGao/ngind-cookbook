
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_filesystem_file.h:

Program Listing for File file.h
===============================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_filesystem_file.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/filesystem/file.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_FILE_H
   #define NGIND_FILE_H
   
   #include <iostream>
   #include <cstdio>
   
   #include "coroutine/coroutine.h"
   #include "memory/auto_collection_object.h"
   
   namespace ngind {
   
   class File : public AutoCollectionObject {
   public:
       File();
       explicit File(const std::string&);
   
       File(const std::string&, const std::string&);
   
       File(const File&) = delete;
       File(File&&) = delete;
   
       ~File();
   
       const static std::string STDIN, STDOUT, STDERR;
   
       void writeLine(const std::string&);
   
       std::string readLine();
   
       void write(const std::string&);
   
       void write(const char*, const size_t&);
   
       char* read(const size_t&);
   
       std::string readToEnd();
   
       inline void flush() {
           fflush(this->_fp);
       }
   
       inline bool isOpen() const {
           return this->_open;
       }
   
       inline bool isReadable() const {
           return this->_readable;
       }
   
       inline bool isWriteable() const {
           return this->_writeable;
       }
   
       inline bool isBinary() const {
           return this->_binary;
       }
   
       void open(const std::string&);
   
       void open(const std::string&, const std::string&);
   
       void close();
   
       Coroutine<char*, const size_t&> readAsync(const size_t&, typename Coroutine<char*, const size_t&>::callback);
   
       Coroutine<void, const std::string&> writeAsync(const std::string&, typename Coroutine<void, const std::string&>::callback);
   
       Coroutine<void, const char*, const size_t&> writeAsync(const char*, const size_t&, typename Coroutine<void, const char*, const size_t&>::callback);
   
   private:
       FILE* _fp;
       bool _open, _readable, _writeable, _binary, _redirect;
   };
   
   } // namespace ngind
   
   #endif //NGIND_FILE_H
