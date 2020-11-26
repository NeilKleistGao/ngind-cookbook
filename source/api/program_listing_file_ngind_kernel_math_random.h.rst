
.. _program_listing_file_ngind_kernel_math_random.h:

Program Listing for File random.h
=================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_math_random.h>` (``ngind/kernel/math/random.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_RANDOM_H
   #define NGIND_RANDOM_H
   
   #include <random>
   
   namespace ngind {
   class Random {
   public:
       Random();
   
       int getRangeRandomNumber(const int&, const int&);
   
       float getPercentageRandomNumber();
   
       float getNormalDistributionRandomNumber(const float&, const float&);
   
   private:
       std::mt19937 _mt;
   
       std::default_random_engine _engine;
   };
   
   }
   
   #endif //NGIND_RANDOM_H
