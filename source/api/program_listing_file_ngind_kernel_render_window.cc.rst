
.. _program_listing_file_ngind_kernel_render_window.cc:

Program Listing for File window.cc
==================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_window.cc>` (``ngind/kernel/render/window.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #include "window.h"
   
   #include "input/input.h"
   
   namespace ngind {
   
   Window::Window(const size_t& width,
           const size_t& height,
           const std::string& title,
           const bool& is_full) : _window(nullptr), _icon(nullptr) {
       glfwInit();
       glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3);
       glfwWindowHint(GLFW_RESIZABLE, GLFW_FALSE);
   
       if (is_full) {
           this->_window = glfwCreateWindow(width, height, title.c_str(), glfwGetPrimaryMonitor(), nullptr);
       }
       else {
           this->_window = glfwCreateWindow(width, height, title.c_str(), nullptr, nullptr);
       }
   
       if (this->_window == nullptr) {
           glfwTerminate();
           exit(-1);
       }
   
       glfwMakeContextCurrent(this->_window);
       Input::getInstance()->setWindowHandler(this->_window);
   }
   
   Window::~Window() {
       glfwDestroyWindow(this->_window);
       this->_window = nullptr;
   
       delete this->_icon;
       this->_icon = nullptr;
   }
   
   void Window::setIcon(const std::string& path) {
       if (this->_icon != nullptr) {
           delete this->_icon;
           this->_icon = nullptr;
       }
   
       this->_icon = new PNGImage(PNGImage::IMAGE_RESOURCE_PATH + "/" + path);
       glfwSetWindowIcon(this->_window, 1, this->_icon->getImageData());
   }
   
   } // namespace ngind
