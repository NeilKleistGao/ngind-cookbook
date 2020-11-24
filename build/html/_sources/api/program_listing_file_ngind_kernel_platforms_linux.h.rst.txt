
.. _program_listing_file_ngind_kernel_platforms_linux.h:

Program Listing for File linux.h
================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_platforms_linux.h>` (``ngind/kernel/platforms/linux.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_LINUX_H
   #define NGIND_LINUX_H
   
   #include <unistd.h>
   
   namespace ngind {
   class PlatformUtils {
   public:
       static inline void sleep(const float& sec) {
           usleep(sec * 1e6);
       }
   };
   
   } // namespace ngind
   
   #endif //NGIND_LINUX_H
