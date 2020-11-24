
.. _program_listing_file_ngind_kernel_input_mouse_input.cc:

Program Listing for File mouse_input.cc
=======================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_input_mouse_input.cc>` (``ngind/kernel/input/mouse_input.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "mouse_input.h"
   
   namespace ngind {
   
   MouseInput::MouseInput(GLFWwindow*& window) {
       glfwSetInputMode(window, GLFW_STICKY_MOUSE_BUTTONS, GLFW_TRUE);
       _pressed.clear();
   }
   
   Vector2D MouseInput::getMousePressed(GLFWwindow*& window, const MouseCode& code) {
       int state = glfwGetMouseButton(window, code);
       if (state == GLFW_PRESS) {
           if (_pressed.find(code) == _pressed.end()) {
               _pressed.insert(code);
               return getMouseMoving(window);
           }
       }
       else {
           if (_pressed.find(code) != _pressed.end()) {
               _pressed.erase(code);
           }
       }
   
       return Vector2D::INVALID;
   }
   
   Vector2D MouseInput::getMouse(GLFWwindow*& window, const MouseCode& code) {
       int state = glfwGetMouseButton(window, code);
       if (state == GLFW_PRESS) {
           if (_pressed.find(code) != _pressed.end()) {
               return getMouseMoving(window);
           }
           else {
               _pressed.insert(code);
           }
       }
       else {
           if (_pressed.find(code) != _pressed.end()) {
               _pressed.erase(code);
           }
       }
   
       return Vector2D::INVALID;
   }
   
   Vector2D MouseInput::getMouseReleased(GLFWwindow*& window, const MouseCode& code) {
       int state = glfwGetMouseButton(window, code);
       if (state == GLFW_PRESS) {
           if (_pressed.find(code) == _pressed.end()) {
               _pressed.insert(code);
           }
       }
       else {
           if (_pressed.find(code) != _pressed.end()) {
               _pressed.erase(code);
               return getMouseMoving(window);
           }
       }
   
       return Vector2D::INVALID;
   }
   
   Vector2D MouseInput::getMouseMoving(GLFWwindow*& window) {
       double x, y;
       glfwGetCursorPos(window, &x, &y);
       return Vector2D(static_cast<float>(x), static_cast<float>(y));
   }
   
   } // namespace
