
.. _program_listing_file_ngind_kernel_input_mouse_input.h:

Program Listing for File mouse_input.h
======================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_input_mouse_input.h>` (``ngind/kernel/input/mouse_input.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_MOUSE_INPUT_H
   #define NGIND_MOUSE_INPUT_H
   
   #include "glfw3.h"
   
   #include "math/vector.h"
   
   #include <set>
   
   namespace ngind {
   
   enum MouseCode {
       BUTTON_LEFT = GLFW_MOUSE_BUTTON_LEFT,
       BUTTON_RIGHT = GLFW_MOUSE_BUTTON_RIGHT,
       BUTTON_MIDDLE = GLFW_MOUSE_BUTTON_MIDDLE
   };
   
   class MouseInput {
   public:
       explicit MouseInput(GLFWwindow*&);
   
       ~MouseInput() = default;
   
       Vector2D getMousePressed(GLFWwindow*&, const MouseCode&);
   
       Vector2D getMouse(GLFWwindow*&, const MouseCode&);
   
       Vector2D getMouseReleased(GLFWwindow*&, const MouseCode&);
   
       Vector2D getMouseMoving(GLFWwindow*&);
   private:
       std::set<MouseCode> _pressed;
   };
   
   } // namespace ngind
   
   #endif //NGIND_MOUSE_INPUT_H
