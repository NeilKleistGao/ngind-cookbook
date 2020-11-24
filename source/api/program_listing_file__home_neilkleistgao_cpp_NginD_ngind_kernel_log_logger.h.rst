
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_log_logger.h:

Program Listing for File logger.h
=================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_log_logger.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/log/logger.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_LOGGER_H
   #define NGIND_LOGGER_H
   
   #include <iostream>
   #include <cstdio>
   
   #include "log_level.h"
   #include "filesystem/output_stream.h"
   
   namespace ngind {
   class Logger {
   public:
       Logger(const std::string&, const LogLevel&);
   
       ~Logger();
   
       const static std::string& STDOUT, &STDERR;
   
       template<typename T>
       void log(const T& msg, const LogLevel& level = LogLevel::LOG_LEVEL_DEBUG) {
           if (level < this->_level) {
               return;
           }
   
           std::string format;
           switch (level) {
               case LOG_LEVEL_INFO:
                   format = _info_format;
                   break;
               case LOG_LEVEL_DEBUG:
                   format = _debug_format;
                   break;
               case LOG_LEVEL_WARNING:
                   format = _warning_format;
                   break;
               case LOG_LEVEL_ERROR:
                   format = _error_format;
                   break;
           }
   
           if (format.empty()) {
               _stream << msg;
           }
           else {
               int pos = format.find('%');
               _stream << format.substr(0,pos) << msg << format.substr(pos + 1);
           }
       }
   
       inline void close() {
           if (_stream.isOpen()) {
               _stream.close();
           }
       }
   private:
       constexpr static char STD_INFO_FORMAT[] = "\033[34m[info]\033[0m %\n";
   
       constexpr static char STD_DEBUG_FORMAT[] = "\033[35m[debug]\033[0m %\n";
   
       constexpr static char STD_WARNING_FORMAT[] = "\033[33m[warning] %\033[0m\n";
   
       constexpr static char STD_ERROR_FORMAT[] = "\033[31m[error] %\033[0m\n";
   
       constexpr static char INFO_FORMAT[] = "[info] %\n";
   
       constexpr static char DEBUG_FORMAT[] = "[debug] %\n";
   
       constexpr static char WARNING_FORMAT[] = "[warning] %\n";
   
       constexpr static char ERROR_FORMAT[] = "[error] %\n";
   
       char* _info_format;
   
       char* _debug_format;
   
       char* _warning_format;
   
       char* _error_format;
   
       OutputStream _stream;
   
       LogLevel _level;
   };
   } // namespace ngind
   
   #endif //NGIND_LOGGER_H
