
.. _program_listing_file_ngind_kernel_objects_world.h:

Program Listing for File world.h
================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_objects_world.h>` (``ngind/kernel/objects/world.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_WORLD_H
   #define NGIND_WORLD_H
   
   #include <string>
   
   #include "object.h"
   #include "components/component.h"
   #include "resources/config_resource.h"
   #include "render/rgba.h"
   
   namespace ngind {
   
   class World : public Object {
   public:
       explicit World(std::string);
   
       inline std::string getName() {
           return _name;
       }
   
       inline RGBA getBackgroundColor() const {
           return _background_color;
       }
   
       inline void setBackgroundColor(const RGBA& color) {
           _background_color = color;
       }
   
       inline void setBackgroundColor(const std::string& code) {
           _background_color = RGBA{code};
       }
   
       void update(const float&) override;
   private:
       std::string _name;
   
       ConfigResource* _config;
   
       RGBA _background_color;
   
       void loadObjects();
   
       Object* generateObject(Object*, const typename ConfigResource::JsonObject&);
   
       Component* generateComponent(const typename ConfigResource::JsonObject&);
   };
   
   } // namespace ngind
   
   #endif //NGIND_WORLD_H
