
.. _program_listing_file_ngind_kernel_objects_world.cc:

Program Listing for File world.cc
=================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_objects_world.cc>` (``ngind/kernel/objects/world.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "world.h"
   
   #include "resources/resources_manager.h"
   #include "entity_object.h"
   #include "rttr/registration.h"
   
   namespace ngind {
   
   World::World(std::string name) : _name(std::move(name)), _config(nullptr), _background_color() {
       _config = ResourcesManager::getInstance()->load<ConfigResource>("world-" + _name + ".json");
       _background_color = RGBA(_config->getDocument()["background-color"].GetString());
   
       loadObjects();
   }
   
   void World::update(const float& delta) {
       Object::update(delta);
   }
   
   void World::loadObjects() {
       auto children = _config->getDocument()["children"].GetArray();
   
       for (const auto& child : children) {
           Object* obj = generateObject(this, child);
           this->addChild(child["name"].GetString(), obj);
       }
   }
   
   Object* World::generateObject(Object* self, const typename ConfigResource::JsonObject& data) {
       Object* object = nullptr;
       if (std::string(data["type"].GetString()) == "entity") {
           object = new EntityObject();
           auto* entity = static_cast<EntityObject*>(object);
   
           auto position = data["position"].GetObject();
           entity->setPositionX(position["x"].GetFloat());
           entity->setPositionY(position["y"].GetFloat());
   
           auto scale = data["scale"].GetObject();
           entity->setScaleX(scale["x"].GetFloat());
           entity->setScaleY(scale["y"].GetFloat());
   
           entity->setRotation(data["rotate"].GetFloat());
           entity->setZOrder(data["z-order"].GetInt());
       }
       else {
           object = new Object();
       }
   
       if (data.HasMember("components")) {
           auto components = data["components"].GetArray();
           for (const auto& com : components) {
               Component* next = generateComponent(com);
               object->addComponent(com["name"].GetString(), next);
           }
       }
       if (data.HasMember("children")) {
           auto children = data["children"].GetArray();
           for (const auto& child : children) {
               Object* next = generateObject(object, child);
               self->addChild(child["name"].GetString(), next);
           }
       }
   
       return object;
   }
   
   Component* World::generateComponent(const typename ConfigResource::JsonObject& data) {
       rttr::type type = rttr::type::get_by_name(data["name"].GetString());
       rttr::variant temp = type.create();
       rttr::method create_func = type.get_method("create");
       rttr::variant var = create_func.invoke(temp, data);
   
       Component* com = var.get_value<Component*>();
       com->init(data);
       return com;
   }
   
   } // namespace ngind
