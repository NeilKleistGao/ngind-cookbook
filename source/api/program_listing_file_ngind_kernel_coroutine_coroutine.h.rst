
.. _program_listing_file_ngind_kernel_coroutine_coroutine.h:

Program Listing for File coroutine.h
====================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_coroutine_coroutine.h>` (``ngind/kernel/coroutine/coroutine.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_COROUTINE_H
   #define NGIND_COROUTINE_H
   
   #include <functional>
   #include <boost/fiber/all.hpp>
   #include <utility>
   
   namespace ngind {
   
   template <typename Type, typename ... Param>
   class Coroutine {
   public:
       using task = std::function<Type(Param ...)>;
       using callback = std::function<void(Type)>;
   
       explicit Coroutine(task task_func) : Coroutine(task_func, nullptr) {
       }
   
       Coroutine(task task_func, callback callback_func) : _process(task_func), _callback(callback_func) {
       }
   
       void run(Param ... param) {
           if (this->_callback == nullptr) { // if this coroutine doesn't have a callback function
               _fiber = boost::fibers::fiber(boost::fibers::launch::dispatch, _process, param...);
           }
           else {
               task temp_task = this->_process;
               callback temp_callback = this->_callback;
               _fiber = boost::fibers::fiber(boost::fibers::launch::dispatch, [&]() {
                   temp_callback(temp_task(param...));
               });
           }
           _fiber.detach();
       }
   
       void wait() {
           if (this->isRunning()) {
               _fiber.join();
           }
       }
   
       inline bool isRunning() {
           return _fiber.joinable();
       }
   
   private:
       boost::fibers::fiber _fiber;
       task _process;
       callback _callback;
   };
   
   template <typename ... Param>
   class Coroutine<void, Param...> {
   public:
       using task = std::function<void(Param ...)>;
       using callback = std::function<void(void)>;
   
       explicit Coroutine(task task_func) : Coroutine(task_func, nullptr) {
       }
   
       Coroutine(task task_func, callback callback_func) : _process(task_func), _callback(std::move(callback_func)) {
       }
   
       void run(Param ... param) {
           if (this->_callback == nullptr) {
               _fiber = boost::fibers::fiber(boost::fibers::launch::dispatch, _process, param...);
           }
           else {
               task temp_task = this->_process;
               callback temp_callback = this->_callback;
               _fiber = boost::fibers::fiber(boost::fibers::launch::dispatch, [&]() {
                   temp_task(param...);
                   temp_callback();
               });
           }
           _fiber.detach();
       }
   
       void wait() {
           if (this->isRunning()) {
               _fiber.join();
           }
       }
   
       inline bool isRunning() {
           return _fiber.joinable();
       }
   
   private:
       boost::fibers::fiber _fiber;
       task _process;
       callback _callback;
   };
   
   template <typename Type>
   class Coroutine<Type, void> {
   public:
       using task = std::function<Type(void)>;
       using callback = std::function<void(const Type&)>;
   
       explicit Coroutine(task task_func) : Coroutine(task_func, nullptr) {
       }
   
       Coroutine(task task_func, callback callback_func) : _process(task_func), _callback(callback_func) {
       }
   
       void run() {
           if (this->_callback == nullptr) {
               _fiber = boost::fibers::fiber(boost::fibers::launch::dispatch, _process);
           }
           else {
               task temp_task = this->_process;
               callback temp_callback = this->_callback;
               _fiber = boost::fibers::fiber(boost::fibers::launch::dispatch, [&temp_task, &temp_callback]() {
                   temp_callback(temp_task());
               });
           }
           _fiber.detach();
       }
   
       void wait() {
           if (this->isRunning()) {
               _fiber.join();
           }
       }
   
       inline bool isRunning() {
           return _fiber.joinable();
       }
   
   private:
       boost::fibers::fiber _fiber;
       task _process;
       callback _callback;
   };
   
   template <>
   class Coroutine<void, void>
   {
   public:
       using task = std::function<void(void)>;
       using callback = std::function<void(void)>;
   
       explicit Coroutine(task task_func) : Coroutine(task_func, nullptr) {
       }
   
       Coroutine(task task_func, callback callback_func) : _process(task_func), _callback(callback_func) {
       }
   
       void run() {
           if (this->_callback == nullptr) {
               _fiber = boost::fibers::fiber(boost::fibers::launch::dispatch, _process);
           }
           else {
               task temp_task = this->_process;
               callback temp_callback = this->_callback;
               _fiber = boost::fibers::fiber(boost::fibers::launch::dispatch, [&temp_task, &temp_callback]() {
                   temp_task();
                   temp_callback();
               });
           }
           _fiber.detach();
       }
   
       void wait() {
           if (this->isRunning()) {
               _fiber.join();
           }
       }
   
       inline bool isRunning() {
           return _fiber.joinable();
       }
   private:
       boost::fibers::fiber _fiber;
       task _process;
       callback _callback;
   };
   } // namespace ngind
   
   #endif //NGIND_COROUTINE_H
