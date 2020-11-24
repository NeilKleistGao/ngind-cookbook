
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_utils_converter.h:

Program Listing for File converter.h
====================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_utils_converter.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/utils/converter.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_CONVERTER_H
   #define NGIND_CONVERTER_H
   
   #include <iostream>
   #include <sstream>
   
   namespace ngind {
   
   class Converter {
   public:
       template <typename Type>
       static Type convertFromString(const std::string& str) {
           std::stringstream stream;
           Type t;
           stream << str;
           stream >> t;
   
           return t;
       }
   
       static unsigned int convertHexString(const std::string&);
   };
   
   } // namespace ngind
   
   #endif //NGIND_CONVERTER_H
