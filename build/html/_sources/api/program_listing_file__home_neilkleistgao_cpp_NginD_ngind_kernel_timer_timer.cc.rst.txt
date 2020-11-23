
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_timer_timer.cc:

Program Listing for File timer.cc
=================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_timer_timer.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/timer/timer.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #include "timer.h"
   
   #include "platforms/platforms.h"
   
   namespace ngind {
   
   Timer::Timer(const float& scale)
       : _time_scale(scale), _local_clock(0.0f), _paused(false), _pause_used(0.0f) {
   }
   
   void Timer::pause() {
       this->_paused = true;
       this->_pause_start = getNow();
       this->_pause_used = 0.0f;
   }
   
   void Timer::resume() {
       this->_paused = false;
       this->_pause_end = getNow();
       std::chrono::duration<float> duration = _pause_end - _pause_start;
       this->_pause_used = duration.count();
   }
   
   void Timer::sleep(const float& sec) {
       if (this->_paused) {
           return;
       }
   
       PlatformUtils::sleep(sec);
       _previous = getNow();
   }
   
   float Timer::getTick() {
       if (this->_paused) {
           return 0.0f;
       }
   
       time_type now = getNow();
       std::chrono::duration<float> duration = now - _previous;
       this->_previous = now;
       float local_duration = (duration.count() - _pause_used) * _time_scale;
       this->_pause_used = 0.0f;
       this->_local_clock += local_duration;
   
       return local_duration;
   }
   
   } // namespace ngind
