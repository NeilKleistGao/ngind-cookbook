
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_platforms_platforms.h:

Program Listing for File platforms.h
====================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_platforms_platforms.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/platforms/platforms.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_PLATFORMS_H
   
   #ifdef PLATFORM_LINUX
   #include "linux.h"
   #elif PLATFORM_WINDOWS
   #include "windows.h"
   #endif
   
   #define NGIND_PLATFORMS_H
   
   #endif //NGIND_PLATFORMS_H
