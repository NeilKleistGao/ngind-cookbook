
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_math_random.cc:

Program Listing for File random.cc
==================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_math_random.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/math/random.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // LAST MODIFY: 2020/8/30
   // FILENAME: random.cc
   
   #include "random.h"
   
   #include <chrono>
   
   namespace ngind {
   
   Random::Random() {
       std::random_device rd;
       this->_mt = std::mt19937 (rd());
   
       unsigned int seed = std::chrono::system_clock::now().time_since_epoch().count();
       this->_engine = std::default_random_engine(seed);
   }
   
   int Random::getRangeRandomNumber(const int& min, const int& max) {
       int len = max - min,
           res = this->_mt() % len;
       return min + res;
   }
   
   float Random::getPercentageRandomNumber() {
       int res = this->_mt();
       return (float)res / (float)(0x7fffffff);
   }
   
   float Random::getNormalDistributionRandomNumber(const float& std, const float& mean) {
       std::normal_distribution dis(mean, std);
       return dis(this->_engine);
   }
   
   } // namespace ngind
