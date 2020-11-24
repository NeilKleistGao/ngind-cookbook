
.. _program_listing_file_ngind_kernel_memory_memory_pool.cc:

Program Listing for File memory_pool.cc
=======================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_memory_memory_pool.cc>` (``ngind/kernel/memory/memory_pool.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "memory_pool.h"
   
   #include <iostream>
   
   namespace ngind {
   MemoryPool* MemoryPool::_instance = nullptr;
   
   MemoryPool* MemoryPool::getInstance() {
       if (_instance == nullptr) {
           _instance = new(std::nothrow) MemoryPool();
       }
   
       return _instance;
   }
   
   void MemoryPool::destroyInstance() {
       delete _instance;
       _instance = nullptr;
   }
   
   void MemoryPool::clear() {
       for (auto it : this->_pool) {
           delete it;
           it = nullptr;
       }
   
       this->_pool.clear();
   }
   
   MemoryPool::MemoryPool() {
       this->_pool.clear();
   }
   
   MemoryPool::~MemoryPool() {
       this->clear();
   }
   
   void MemoryPool::remove(AutoCollectionObject* obj) {
       auto it = this->_pool.find(obj);
       if (it != this->_pool.end()) {
           this->_pool.erase(it);
       }
   }
   
   } // namespace ngind
