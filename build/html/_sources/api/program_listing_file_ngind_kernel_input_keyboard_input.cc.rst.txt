
.. _program_listing_file_ngind_kernel_input_keyboard_input.cc:

Program Listing for File keyboard_input.cc
==========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_input_keyboard_input.cc>` (``ngind/kernel/input/keyboard_input.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "keyboard_input.h"
   
   namespace ngind {
   
   KeyboardInput::KeyboardInput(GLFWwindow* window) {
       glfwSetInputMode(window, GLFW_STICKY_KEYS, GLFW_TRUE);
       this->_pressed.clear();
   }
   
   bool KeyboardInput::getKey(GLFWwindow *window, const KeyboardCode& code) {
       int state = glfwGetKey(window, code);
       if (state == GLFW_PRESS) {
           if (this->_pressed.find(code) == this->_pressed.end()) {
               this->_pressed.insert(code);
           }
           else {
               return true;
           }
       }
       else if (this->_pressed.find(code) != this->_pressed.end()) {
           this->_pressed.erase(code);
       }
   
       return false;
   }
   
   bool KeyboardInput::getKeyPressed(GLFWwindow* window, const KeyboardCode& code) {
       int state = glfwGetKey(window, code);
       if (state == GLFW_PRESS) {
           if (this->_pressed.find(code) == this->_pressed.end()) {
               this->_pressed.insert(code);
               return true;
           }
       }
       else if (this->_pressed.find(code) != this->_pressed.end()) {
           this->_pressed.erase(code);
       }
   
       return false;
   }
   
   bool KeyboardInput::getKeyReleased(GLFWwindow* window, const KeyboardCode& code) {
       int state = glfwGetKey(window, code);
       if (state == GLFW_RELEASE) {
           if (this->_pressed.find(code) != this->_pressed.end()) {
               this->_pressed.erase(code);
               return true;
           }
       }
       else if (this->_pressed.find(code) == this->_pressed.end()) {
           this->_pressed.insert(code);
       }
   
       return false;
   }
   
   } // namespace ngind
