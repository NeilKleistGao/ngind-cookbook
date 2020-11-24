
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_input_text_input.cc:

Program Listing for File text_input.cc
======================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_input_text_input.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/input/text_input.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "text_input.h"
   
   namespace ngind {
   TextInput* TextInput::_self = nullptr;
   
   TextInput::TextInput(GLFWwindow*& win) : _enabled(false) {
       glfwSetCharCallback(win, TextInput::textCallBack);
       TextInput::_self = this;
   }
   
   std::string TextInput::getString(const EncodingType& encoding) {
       std::string res = "";
       for (const auto& ch : _buff) {
           if (encoding == EncodingType::ENCODING_ASCII) {
               res += static_cast<char>(ch);
           }
           else if (encoding == EncodingType::ENCODING_UTF8) {
               res += static_cast<char>(ch & 0x000000FF);
               res += static_cast<char>(ch & 0x0000FF00);
           }
       }
   
       _buff.clear();
       return res;
   }
   
   void TextInput::textCallBack(GLFWwindow*, unsigned int codepoint) {
       if (_self->_enabled) {
           _self->_buff.push_back(codepoint);
       }
   }
   
   } // namespace ngind
