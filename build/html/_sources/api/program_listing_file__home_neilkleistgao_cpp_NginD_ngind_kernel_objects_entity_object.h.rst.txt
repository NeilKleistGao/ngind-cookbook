
.. _program_listing_file__home_neilkleistgao_cpp_NginD_ngind_kernel_objects_entity_object.h:

Program Listing for File entity_object.h
========================================

|exhale_lsh| :ref:`Return to documentation for file <file__home_neilkleistgao_cpp_NginD_ngind_kernel_objects_entity_object.h>` (``/home/neilkleistgao/cpp/NginD/ngind/kernel/objects/entity_object.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_ENTITY_OBJECT_H
   #define NGIND_ENTITY_OBJECT_H
   
   #include "object.h"
   
   #include "math/vector.h"
   
   namespace ngind {
   
   class EntityObject : public Object {
   public:
       EntityObject();
   
       ~EntityObject() = default;
   
       EntityObject(const EntityObject&) = delete;
       EntityObject& operator= (const EntityObject&) = delete;
   
       virtual void update(const float&);
   
       inline void setPosition(const Vector2D& v) {
           _position = v;
       }
   
       inline void setPositionX(const float& f) {
           _position.setX(f);
       }
   
       inline void setPositionY(const float& f) {
           _position.setY(f);
       }
   
       inline Vector2D getPosition() const {
           return _position;
       }
   
       inline float getPositionX() const {
           return _position.getX();
       }
   
       inline float getPositionY() const {
           return _position.getY();
       }
   
       inline void setScale(const Vector2D& v) {
           _scale = v;
       }
   
       inline void setScaleX(const float& f) {
           _scale.setX(f);
       }
   
       inline void setScaleY(const float& f) {
           _scale.setY(f);
       }
   
       inline Vector2D getScale() const {
           return _scale;
       }
   
       inline float getScaleX() const {
           return _scale.getX();
       }
   
       inline float getScaleY() const {
           return _scale.getY();
       }
   
       inline void setRotation(const float& f) {
           _rotation = f;
       }
   
       inline float getRotation() const {
           return _rotation;
       }
   
       inline int getZOrder() const {
           return _z_order;
       }
   
       inline void setZOrder(const int& z) {
           _z_order = z;
       }
   
       inline void addComponent(const std::string& name, Component* component) override {
           if (_components.find(name) == _components.end()) {
               _components[name] = component;
               component->setParent(this);
           }
       }
   
   private:
       Vector2D _position;
   
       Vector2D _scale;
   
       float _rotation;
   
       int _z_order;
   };
   
   
   } // namespace ngind
   
   #endif //NGIND_ENTITY_OBJECT_H
