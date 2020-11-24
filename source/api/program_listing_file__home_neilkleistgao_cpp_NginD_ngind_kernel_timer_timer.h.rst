
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_timer_timer.h:

Program Listing for File timer.h
================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_timer_timer.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/timer/timer.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_TIMER_H
   #define NGIND_TIMER_H
   
   #include <chrono>
   
   namespace ngind {
   
   class Timer {
   public:
       using time_type = std::chrono::time_point<std::chrono::system_clock>;
   
       explicit Timer(const float& scale = 1.0f);
   
       ~Timer() = default;
   
       void pause();
   
       void resume();
   
       void sleep(const float&);
   
       float getTick();
   
       static inline time_type getNow() {
           return std::chrono::system_clock::now();
       }
   
       inline void start() {
           _previous = getNow();
       }
   
       inline void theWorld() {
           //zawarudo! toki o tomare
           this->pause();
       }
   
       inline void setTimeScale(const float& scale) {
           this->_time_scale = scale;
       }
   
       inline const float getTimeScale() const {
           return this->_time_scale;
       }
   
       inline const float GetLocalClock() const {
           return this->_local_clock;
       }
   private:
       float _time_scale;
   
       float _local_clock;
   
       float _pause_used;
   
       time_type _previous;
   
       time_type _pause_start;
   
       time_type _pause_end;
   
       bool _paused;
   };
   
   } // namespace ngind
   
   #endif //NGIND_TIMER_H
