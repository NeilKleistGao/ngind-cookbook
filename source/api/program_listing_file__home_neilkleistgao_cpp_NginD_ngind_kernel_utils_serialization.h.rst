
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_utils_serialization.h:

Program Listing for File serialization.h
========================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_utils_serialization.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/utils/serialization.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: serialization.h
   // LAST MODIFY: 2020/8/16
   
   #ifndef NGIND_SERIALIZATION_H
   #define NGIND_SERIALIZATION_H
   
   // All serialization methods here
   // Use these methods if the object to be serialized is a POD or std container
   // Or you need to implement the Serializable interface and serialize method
   
   #include <iostream>
   #include <sstream>
   #include <type_traits>
   
   namespace ngind {
   
   class Serializable {
   public:
       virtual void serialize(std::ostream&) const = 0;
       virtual void deserialize(std::istream&) = 0;
   };
   
   } // namespace ngind
   
   #endif //NGIND_SERIALIZATION_H
