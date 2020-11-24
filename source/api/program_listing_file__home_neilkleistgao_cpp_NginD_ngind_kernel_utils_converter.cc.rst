
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_utils_converter.cc:

Program Listing for File converter.cc
=====================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_utils_converter.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/utils/converter.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #include "converter.h"
   
   #include <cctype>
   
   namespace ngind {
   
   unsigned int Converter::convertHexString(const std::string& str) {
       unsigned int res = 0;
       for (const auto& ch : str) {
           res <<= 4;
           if (isdigit(ch)) {
               res += static_cast<unsigned int>(ch - '0');
           }
           else if (islower(ch)) {
               res += static_cast<unsigned int>(ch - 'a' + 10);
           }
           else {
               res += static_cast<unsigned int>(ch - 'A' + 10);
           }
       }
   
       return res;
   }
   
   } // namespace ngind
