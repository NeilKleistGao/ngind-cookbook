
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_render_queue.cc:

Program Listing for File render_queue.cc
========================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_render_queue.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/render_queue.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #include "render_queue.h"
   
   #include <algorithm>
   
   namespace ngind {
   
   void RenderQueue::sort() {
       if (_queue.empty()) {
           return;
       }
   
       std::sort(_queue.begin(), _queue.end(),
                 [](RenderCommand* c1, RenderCommand* c2) -> bool {
           return c1->z_order < c2->z_order;
       });
   }
   
   } // namespace
