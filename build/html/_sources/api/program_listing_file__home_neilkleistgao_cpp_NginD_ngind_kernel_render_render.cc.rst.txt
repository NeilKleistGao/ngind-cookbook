
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_render.cc:

Program Listing for File render.cc
==================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_render_render.cc>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/render/render.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #include "GL/glew.h"
   
   #include "render.h"
   #include "perspective.h"
   
   namespace ngind {
   Render* Render::_instance = nullptr;
   
   Render* Render::getInstance() {
       if (_instance == nullptr) {
           _instance = new Render();
       }
   
       return _instance;
   }
   
   void Render::destroyInstance() {
       if (_instance != nullptr) {
           delete _instance;
           _instance = nullptr;
       }
   
       glfwTerminate();
   }
   
   Render::Render()
       : _window(nullptr), _queue(nullptr) {
       _queue = new RenderQueue();
   }
   
   Render::~Render() {
       delete _window;
       _window = nullptr;
   }
   
   bool Render::startRenderLoopOnce() {
       if (this->_window->isLoopEnd()) {
           return false;
       }
   
       _queue->sort();
       for (auto cmd : (*_queue)) {
           this->execute(cmd);
       }
   
       _queue->clear();
       this->_window->swapBuffer();
       return true;
   }
   
   void Render::createWindow(const int& width,
                     const int& height,
                     const std::string& title,
                     const std::string& icon,
                     const bool& is_full) {
       this->_window = new Window(width, height, title, is_full);
       this->_window->setIcon(icon);
   
       glewExperimental = GL_TRUE;
       if (glewInit() != GLEW_OK) {
           //TODO: init error
           exit(-1);
       }
   
       glEnable(GL_BLEND);
       glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);
       Perspective::getInstance()->init({width / 2.0f, height / 2.0f}, width, height);
   }
   
   void Render::execute(RenderCommand* cmd) {
       switch (cmd->type) {
           case RenderCommandType::QUAD_COMMAND:
               drawQuad(static_cast<QuadRenderCommand*>(cmd));
               break;
           default:
               break;
       }
   }
   
   void Render::drawQuad(QuadRenderCommand* cmd) {
       glBindTexture(GL_TEXTURE_2D, cmd->texture_id);
       cmd->program->use();
       glBindVertexArray(cmd->quad->getVAO());
       glDrawElements(GL_TRIANGLES, 6, GL_UNSIGNED_INT, 0);
       glBindVertexArray(0);
   }
   
   } // namespace ngind
