
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_log_logger_factory.h:

Program Listing for File logger_factory.h
=========================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_log_logger_factory.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/log/logger_factory.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_LOGGER_FACTORY_H
   #define NGIND_LOGGER_FACTORY_H
   
   #include <map>
   #include <string>
   
   #include "logger.h"
   
   namespace ngind {
   class LoggerFactory {
   public:
       static LoggerFactory* getInstance();
   
       static void destroyInstance();
   
       Logger* getLogger(const std::string&, const LogLevel&);
   private:
       LoggerFactory() = default;
   
       ~LoggerFactory();
   
       static LoggerFactory* _instance;
   
       std::map<std::string, Logger*> _loggers;
   };
   } // namespace ngind
   
   #endif //NGIND_LOGGER_FACTORY_H
