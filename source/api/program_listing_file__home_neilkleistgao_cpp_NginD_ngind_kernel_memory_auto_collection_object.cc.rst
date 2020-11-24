
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_memory_auto_collection_object.cc:

Program Listing for File auto_collection_object.cc
==================================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_memory_auto_collection_object.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/memory/auto_collection_object.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "auto_collection_object.h"
   #include "memory_pool.h"
   
   namespace ngind {
   
   AutoCollectionObject::AutoCollectionObject() : _sustain(0) {
       MemoryPool::getInstance()->insert(this);
   }
   
   void AutoCollectionObject::removeReference() {
       this->_sustain--;
   
       if (this->_sustain == 0) {
           MemoryPool::getInstance()->remove(this);
       }
   }
   
   } // namespace ngind
