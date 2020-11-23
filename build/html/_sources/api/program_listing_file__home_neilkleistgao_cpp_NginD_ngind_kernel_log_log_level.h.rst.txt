
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_log_log_level.h:

Program Listing for File log_level.h
====================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_log_log_level.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/log/log_level.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #ifndef NGIND_LOG_LEVEL_H
   #define NGIND_LOG_LEVEL_H
   
   namespace ngind {
   
   enum LogLevel {
       LOG_LEVEL_INFO = 0,
       LOG_LEVEL_DEBUG = 1,
       LOG_LEVEL_WARNING = 2,
       LOG_LEVEL_ERROR = 3
   };
   } // namespace ngind
   
   #endif //NGIND_LOG_LEVEL_H
