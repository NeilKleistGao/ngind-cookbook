
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_input_input.h:

Program Listing for File input.h
================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_input_input.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/input/input.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_INPUT_H
   #define NGIND_INPUT_H
   
   #include "keyboard_input.h"
   #include "mouse_input.h"
   #include "text_input.h"
   
   #include "render/window.h"
   
   namespace ngind {
   
   
   class Input {
   public:
       static Input* getInstance();
   
       static void destroyInstance();
   
       inline bool getKey(const KeyboardCode& code) {
           return !_text_mod && this->_keyboard->getKey(this->_window_handler, code);
       }
   
       inline bool getKeyPressed(const KeyboardCode& code) {
           return !_text_mod && this->_keyboard->getKeyPressed(this->_window_handler, code);
       }
   
       inline bool getKeyReleased(const KeyboardCode& code) {
           return !_text_mod && this->_keyboard->getKeyReleased(this->_window_handler, code);
       }
   
       inline Vector2D getMousePressed(const MouseCode& code) {
           return this->_mouse->getMousePressed(_window_handler, code);
       }
   
       inline Vector2D getMouse(const MouseCode& code) {
           return this->_mouse->getMouse(_window_handler, code);
       }
   
       inline Vector2D getMouseReleased(const MouseCode& code) {
           return this->_mouse->getMouseReleased(_window_handler, code);
       }
   
       inline Vector2D getMouseMoving() {
           return this->_mouse->getMouseMoving(_window_handler);
       }
   
       inline std::string getString(const EncodingType& encoding) {
           if (!_text_mod) {
               return "";
           }
           return this->_text->getString(encoding);
       }
   
       inline void switchTextMod(const bool& is_enable) {
           _text_mod = is_enable;
       }
   
       friend class Window;
   private:
       static Input* _instance;
   
       KeyboardInput* _keyboard;
   
       MouseInput* _mouse;
   
       TextInput* _text;
   
       GLFWwindow* _window_handler;
   
       bool _text_mod;
   
       inline void setWindowHandler(GLFWwindow* window) {
           _window_handler = window;
           this->_keyboard = new KeyboardInput(window);
           this->_mouse = new MouseInput(window);
           this->_text = new TextInput(window);
       }
   
       Input();
   
       ~Input();
   };
   
   } // namespace ngind
   
   #endif //NGIND_INPUT_H
