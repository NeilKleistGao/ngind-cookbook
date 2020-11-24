
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_perspective.cc:

Program Listing for File perspective.cc
=======================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_perspective.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/perspective.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "perspective.h"
   
   #include <iostream>
   
   #include "resources/program_resource.h"
   
   namespace ngind {
   Perspective* Perspective::_instance = nullptr;
   
   Perspective::Perspective() : _width(0), _height(0) {
   }
   
   Perspective* Perspective::getInstance() {
       if (_instance == nullptr) {
           _instance = new(std::nothrow) Perspective();
   
           if (_instance == nullptr) {
               // TODO: throw
           }
       }
   
       return _instance;
   }
   
   void Perspective::destroyInstance() {
       if (_instance != nullptr) {
           delete _instance;
           _instance = nullptr;
       }
   }
   
   void Perspective::init(const Vector2D& center, const size_t& width, const size_t& height) {
       glViewport(center.getX() - width / 2, center.getY() - height / 2,
                  width, height);
       _projection = glm::ortho(0.0f, static_cast<float>(width),
                                         static_cast<float>(height), 0.0f,
                                         -1.0f, 1.0f); //TODO:
   
       _width = width; _height = height;
   }
   } // namespace ngind
