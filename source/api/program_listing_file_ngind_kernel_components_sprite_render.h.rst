
.. _program_listing_file_ngind_kernel_components_sprite_render.h:

Program Listing for File sprite_render.h
========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_components_sprite_render.h>` (``ngind/kernel/components/sprite_render.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_SPRITE_RENDER_H
   #define NGIND_SPRITE_RENDER_H
   
   #include <string>
   
   #include "render/render_command.h"
   #include "render_component.h"
   #include "resources/texture_resource.h"
   #include "math/vector.h"
   #include "render/rgba.h"
   #include "render/program.h"
   #include "render/quad.h"
   #include "objects/entity_object.h"
   #include "resources/program_resource.h"
   
   #include "rttr/registration.h"
   
   namespace ngind {
   
   class SpriteRender : public RenderComponent {
   public:
       SpriteRender();
       ~SpriteRender() override;
       SpriteRender(const SpriteRender&) = delete;
       SpriteRender& operator= (const SpriteRender&) = delete;
   
       void update(const float&) override;
   
       void init(const typename ConfigResource::JsonObject&) override;
   
       static SpriteRender* create(const typename ConfigResource::JsonObject&);
   
       void setImage(const std::string&);
   
       void setImage(const std::string&, const Vector2D&, const Vector2D&);
   
       inline std::string getImageName() {
           return _texture->getResourcePath();
       }
   
       inline void setBound(const Vector2D& lb, const Vector2D& rt) {
           setLeftBottomBound(lb);
           setRightTopBound(rt);
       }
   
       inline void setLeftBottomBound(const Vector2D& lb) {
           _lb = lb;
       }
   
       inline void setRightTopBound(const Vector2D& rt) {
           _rt = rt;
       }
   
       inline Vector2D getLeftBottomBound() const {
           return _lb;
       }
   
       inline Vector2D getRightTopBound() const {
           return _rt;
       }
   
       inline void setColor(const RGBA& color) {
           _color = color;
       }
   
       inline RGBA getColor() const {
           return _color;
       }
   
   private:
       TextureResource* _texture;
   
       Vector2D _lb, _rt;
   
       RGBA _color;
   
       QuadRenderCommand* _command;
   
       ProgramResource* _program;
   
       Quad* _quad;
   
   protected:
       virtual void draw();
   };
   
   RTTR_REGISTRATION {
       rttr::registration::class_<SpriteRender>("SpriteRender")
           .method("create", &SpriteRender::create);
   }
   
   } // namespace ngind
   
   #endif //NGIND_SPRITE_RENDER_H
