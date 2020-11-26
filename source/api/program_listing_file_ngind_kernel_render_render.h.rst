
.. _program_listing_file_ngind_kernel_render_render.h:

Program Listing for File render.h
=================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_render.h>` (``ngind/kernel/render/render.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_RENDER_H
   #define NGIND_RENDER_H
   
   #include "render_queue.h"
   #include "window.h"
   #include "rgba.h"
   #include "perspective.h"
   
   namespace ngind {
   
   class Render {
   public:
       static Render* getInstance();
   
       static void destroyInstance();
   
       bool startRenderLoopOnce();
   
       void createWindow(const int&, const int&, const std::string&, const std::string&, const bool&);
   
       inline void clearScene(const RGBA& color) {
           glClearColor(color.r / 255.0f, color.g / 255.0f, color.b / 255.0f, color.a / 255.0f);
           glClear(GL_COLOR_BUFFER_BIT);
       }
   
       inline void addRenderCommand(RenderCommand* cmd) {
           _queue->push(cmd);
       }
   
   private:
       static Render* _instance;
   
       Window* _window;
   
       RenderQueue* _queue;
   
       void execute(RenderCommand*);
   
       void drawQuad(QuadRenderCommand*);
   
       Render();
   
       ~Render();
   };
   
   } // namespace ngind
   
   #endif //NGIND_RENDER_H
