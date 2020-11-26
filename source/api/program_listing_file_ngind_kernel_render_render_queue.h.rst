
.. _program_listing_file_ngind_kernel_render_render_queue.h:

Program Listing for File render_queue.h
=======================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_render_queue.h>` (``ngind/kernel/render/render_queue.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_RENDER_QUEUE_H
   #define NGIND_RENDER_QUEUE_H
   
   #include "render_command.h"
   
   #include <vector>
   
   namespace ngind {
   
   class RenderQueue {
   public:
       RenderQueue() = default;
   
       ~RenderQueue() = default;
   
       using iterator = std::vector<RenderCommand*>::iterator;
   
       inline iterator begin() {
           return _queue.begin();
       }
   
       inline iterator end() {
           return _queue.end();
       }
   
       inline void clear() {
           _queue.clear();
       }
   
       inline void push(RenderCommand* command) {
           _queue.push_back(command);
       }
   
       void sort();
   
   private:
       std::vector<RenderCommand*> _queue;
   };
   
   } // namespace
   
   #endif //NGIND_RENDER_QUEUE_H
