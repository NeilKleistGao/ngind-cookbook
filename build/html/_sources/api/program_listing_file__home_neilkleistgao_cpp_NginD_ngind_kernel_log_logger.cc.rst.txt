
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_log_logger.cc:

Program Listing for File logger.cc
==================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_log_logger.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/log/logger.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #include "logger.h"
   
   namespace ngind {
   const std::string& Logger::STDOUT = OutputStream::STDOUT;
   const std::string& Logger::STDERR = OutputStream::STDERR;
   
   Logger::Logger(const std::string& filename, const LogLevel& level) : _stream(filename), _level(level) {
       if (filename == OutputStream::STDOUT ||
           filename == OutputStream::STDERR) {
           this->_info_format = const_cast<char*>(STD_INFO_FORMAT);
           this->_debug_format = const_cast<char*>(STD_DEBUG_FORMAT);
           this->_warning_format = const_cast<char*>(STD_WARNING_FORMAT);
           this->_error_format = const_cast<char*>(STD_ERROR_FORMAT);
       }
       else {
           this->_info_format = const_cast<char*>(INFO_FORMAT);
           this->_debug_format = const_cast<char*>(DEBUG_FORMAT);
           this->_warning_format = const_cast<char*>(WARNING_FORMAT);
           this->_error_format = const_cast<char*>(ERROR_FORMAT);
       }
   }
   
   Logger::~Logger() {
       this->close();
   }
   } // namespace ngind
