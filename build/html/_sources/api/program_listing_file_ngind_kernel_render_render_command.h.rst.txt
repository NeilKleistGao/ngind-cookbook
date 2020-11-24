
.. _program_listing_file_ngind_kernel_render_render_command.h:

Program Listing for File render_command.h
=========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_render_command.h>` (``ngind/kernel/render/render_command.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: render_command.h
   // LAST MODIFY: 2020/11/1
   
   #ifndef NGIND_RENDER_COMMAND_H
   #define NGIND_RENDER_COMMAND_H
   
   #include "quad.h"
   #include "program.h"
   #include "math/vector.h"
   #include "rgba.h"
   
   namespace ngind {
   
   enum RenderCommandType {
       UNKNOWN_COMMAND,
       QUAD_COMMAND,
       // TODO: other types
   };
   
   struct RenderCommand {
   public:
       unsigned int z_order{};
       const RenderCommandType type;
       bool transparent{};
   
       explicit RenderCommand(const RenderCommandType& t = UNKNOWN_COMMAND)
           : type(t) {}
   };
   
   struct QuadRenderCommand : public RenderCommand {
       GLuint texture_id{};
       Quad* quad;
       Program* program;
   
       QuadRenderCommand()
           : RenderCommand(QUAD_COMMAND), quad(nullptr), program(nullptr) {}
   };
   
   } // namespace ngind
   
   #endif //NGIND_RENDER_COMMAND_H
