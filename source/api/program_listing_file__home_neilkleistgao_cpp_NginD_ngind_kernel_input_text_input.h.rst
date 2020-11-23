
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_input_text_input.h:

Program Listing for File text_input.h
=====================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_input_text_input.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/input/text_input.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_TEXT_INPUT_H
   #define NGIND_TEXT_INPUT_H
   
   #include <string>
   #include <list>
   
   #include "glfw3.h"
   
   namespace ngind {
   
   enum EncodingType {
       ENCODING_ASCII,
       ENCODING_UTF8 
   };
   
   class TextInput {
   public:
       explicit TextInput(GLFWwindow*&);
   
       ~TextInput() = default;
   
       std::string getString(const EncodingType& encoding = EncodingType::ENCODING_ASCII);
   
       inline void setEnable(const bool& enable) {
           _enabled = enable;
       }
   private:
   
       static void textCallBack(GLFWwindow*, unsigned int);
   
       std::list<unsigned int> _buff;
   
       static TextInput* _self;
   
       bool _enabled;
   };
   
   } // namespace ngind
   
   #endif //NGIND_TEXT_INPUT_H
