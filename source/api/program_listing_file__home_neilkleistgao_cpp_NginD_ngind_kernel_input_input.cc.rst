
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_input_input.cc:

Program Listing for File input.cc
=================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_input_input.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/input/input.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "input.h"
   
   namespace ngind {
   
   Input* Input::_instance = nullptr;
   
   Input* Input::getInstance() {
       if (_instance == nullptr) {
           _instance = new Input();
       }
   
       return _instance;
   }
   
   void Input::destroyInstance() {
       if (_instance != nullptr) {
           delete _instance;
           _instance = nullptr;
       }
   }
   
   Input::Input() :
       _keyboard(nullptr),
       _window_handler(nullptr),
       _mouse(nullptr),
       _text(nullptr),
       _text_mod(false){
   
   }
   
   Input::~Input() {
       delete _keyboard;
       _keyboard = nullptr;
       delete _mouse;
       _mouse = nullptr;
       delete _text;
       _text = nullptr;
   }
   
   } // namespace ngind
