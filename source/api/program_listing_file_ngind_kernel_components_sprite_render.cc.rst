
.. _program_listing_file_ngind_kernel_components_sprite_render.cc:

Program Listing for File sprite_render.cc
=========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_components_sprite_render.cc>` (``ngind/kernel/components/sprite_render.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "sprite_render.h"
   
   #include <vector>
   
   #include "render/render.h"
   #include "render/perspective.h"
   #include "resources/resources_manager.h"
   
   namespace ngind {
   
   SpriteRender::SpriteRender()
           : _color("#FFFFFFFF"), _command(nullptr),
           _quad(nullptr), _program(nullptr),
           _texture(nullptr), _lb(), _rt() {
   }
   
   SpriteRender::~SpriteRender() {
       if (_texture != nullptr) {
           ResourcesManager::getInstance()->release(_texture->getResourcePath());
           delete _texture;
           _texture = nullptr;
       }
   
       if (_program != nullptr) {
           ResourcesManager::getInstance()->release(_program->getResourcePath());
           delete _program;
           _program = nullptr;
       }
   
       if (_quad != nullptr) {
           delete _quad;
           _quad = nullptr;
       }
   }
   
   void SpriteRender::update(const float& delta) {
       RenderComponent::update(delta);
       this->draw();
   }
   
   void SpriteRender::setImage(const std::string& filename) {
       if (_texture->getResourcePath() == filename) {
           return;
       }
   
       if (_texture != nullptr) {
           ResourcesManager::getInstance()->release(_texture->getResourcePath());
       }
       _texture = ResourcesManager::getInstance()->load<TextureResource>(filename);
   }
   
   void SpriteRender::setImage(const std::string& filename, const Vector2D& lb, const Vector2D& rt) {
       this->setImage(filename);
       setBound(lb, rt);
   }
   
   void SpriteRender::draw() {
       if (_parent == nullptr) {
       }
   
       auto temp = static_cast<EntityObject*>(_parent);
       auto pos = temp->getPosition();
       auto sz = _texture->getTextureSize();
   
       if (_command == nullptr) {
           _command = new QuadRenderCommand();
       }
   
       if (_quad == nullptr) {
           auto color_size = (_texture->getTextureColorMode() == TextureColorMode::MODE_RGB) ? 3 : 4;
           auto bound = Perspective::getInstance()->getPerspectiveSize() * 0.5f;
           auto texture_size = _texture->getTextureSize();
   
           _quad = new Quad({
                   (pos.getX() + texture_size.getX() / 2 - bound.getX()) / bound.getX(), (pos.getY() + texture_size.getY() / 2 - bound.getY()) / bound.getY(), 0.0f,  1.0f, 0.0f, 0.0f, 1.0f, 0.0f, // Top Right
                   (pos.getX() + texture_size.getX() / 2 - bound.getX()) / bound.getX(), (pos.getY() - texture_size.getY() / 2 - bound.getY()) / bound.getY(), 0.0f,  0.0f, 1.0f, 0.0f, 1.0f, 1.0f, // Bottom Right
                   (pos.getX() - texture_size.getX() / 2 - bound.getX()) / bound.getX(), (pos.getY() - texture_size.getY() / 2 - bound.getY()) / bound.getY(), 0.0f,  0.0f, 0.0f, 1.0f, 0.0f, 1.0f, // Bottom Left
                   (pos.getX() - texture_size.getX() / 2 - bound.getX()) / bound.getX(), (pos.getY() + texture_size.getY() / 2 - bound.getY()) / bound.getY(), 0.0f,  0.0f, 0.0f, 0.0f, 0.0f, 0.0f  // Top Left
           }, color_size);
       }
   
       _command->quad = _quad;
       _command->texture_id = _texture->getTextureID();
       _command->z_order = temp->getZOrder();
       _command->transparent = false;
       _command->program = _program->getProgram();
   
       Render::getInstance()->addRenderCommand(_command);
   }
   
   void SpriteRender::init(const typename ConfigResource::JsonObject& data) {
       std::string name = data["filename"].GetString();
       if (!name.empty()) {
           _texture = ResourcesManager::getInstance()->load<TextureResource>(name);
       }
       if (_program == nullptr) {
           _program = ResourcesManager::getInstance()->load<ProgramResource>("sprite"); // default sprite shader
       }
   }
   
   SpriteRender* SpriteRender::create(const typename ConfigResource::JsonObject& data) {
       auto* com = new SpriteRender();
       com->init(data);
       return com;
   }
   
   } // namespace ngind
