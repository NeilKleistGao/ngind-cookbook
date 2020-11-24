
.. _program_listing_file_ngind_kernel_render_window.h:

Program Listing for File window.h
=================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_window.h>` (``ngind/kernel/render/window.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_WINDOW_H
   #define NGIND_WINDOW_H
   
   #include <iostream>
   #include <cstdio>
   
   #include "include/opengl/glfw3.h"
   
   #include "png_image.h"
   
   namespace ngind {
   
   class Window {
   public:
       Window(const size_t&, const size_t&, const std::string&, const bool& is_full = false);
   
       ~Window();
   
       void setIcon(const std::string&);
   
       inline bool isLoopEnd() {
           return glfwWindowShouldClose(this->_window);
       }
   
       inline void swapBuffer() {
           glfwSwapBuffers(this->_window);
       }
   
       inline std::pair<float, float> getContentScale() {
           float x_scale, y_scale;
           glfwGetWindowContentScale(this->_window, &x_scale, &y_scale);
           return {x_scale, y_scale};
       }
   
       inline void setTitle(const std::string& title) {
           glfwSetWindowTitle(this->_window, title.c_str());
       }
   
       inline void setFullScreen(const bool& is_full) {
           GLFWmonitor* monitor = glfwGetPrimaryMonitor();
           const GLFWvidmode* mode = glfwGetVideoMode(monitor);
   
           if (is_full) {
               glfwSetWindowMonitor(this->_window, monitor, 0, 0, mode->width, mode->height, mode->refreshRate);
           }
           else {
               glfwSetWindowMonitor(this->_window, nullptr, 0, 0, mode->width, mode->height, 0);
           }
       }
   
       inline void resize(const size_t& width, const size_t& height) {
           glfwSetWindowSize(this->_window, width, height);
       }
   
   private:
       GLFWwindow *_window;
   
       PNGImage* _icon;
   };
   } // namespace ngind
   
   #endif //NGIND_WINDOW_H
