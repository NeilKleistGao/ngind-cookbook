
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_components_render_component.h:

Program Listing for File render_component.h
===========================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_components_render_component.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/components/render_component.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_RENDER_COMPONENT_H
   #define NGIND_RENDER_COMPONENT_H
   
   #include "component.h"
   
   namespace ngind {
   
   class RenderComponent : public Component {
   public:
       RenderComponent() = default;
       virtual ~RenderComponent() = default;
       RenderComponent(const RenderComponent&) = delete;
       RenderComponent& operator= (const RenderComponent&) = delete;
   
       virtual void update(const float&) {};
   
       virtual void init(const typename ConfigResource::JsonObject&) {};
   protected:
       virtual void draw() = 0;
   };
   
   } // namespace ngind
   
   #endif //NGIND_RENDER_COMPONENT_H
