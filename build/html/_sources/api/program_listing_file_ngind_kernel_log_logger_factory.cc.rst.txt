
.. _program_listing_file_ngind_kernel_log_logger_factory.cc:

Program Listing for File logger_factory.cc
==========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_log_logger_factory.cc>` (``ngind/kernel/log/logger_factory.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "logger_factory.h"
   
   namespace ngind {
   LoggerFactory* LoggerFactory::_instance = nullptr;
   
   LoggerFactory* LoggerFactory::getInstance() {
       if (_instance == nullptr) {
           _instance = new LoggerFactory();
       }
   
       return _instance;
   }
   
   void LoggerFactory::destroyInstance() {
       if (_instance != nullptr) {
           delete _instance;
           _instance = nullptr;
       }
   }
   
   Logger* LoggerFactory::getLogger(const std::string& filename, const LogLevel& level) {
       if (_loggers.find(filename) != _loggers.end()) {
           return _loggers[filename];
       }
   
       _loggers[filename] = new Logger(filename, level);
       return _loggers[filename];
   }
   
   LoggerFactory::~LoggerFactory() {
       for (auto pairs : _loggers) {
           delete pairs.second;
           pairs.second = nullptr;
       }
   
       _loggers.clear();
   }
   
   } // namespace ngind
