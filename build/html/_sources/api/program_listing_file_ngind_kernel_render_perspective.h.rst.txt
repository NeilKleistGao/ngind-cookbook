
.. _program_listing_file_ngind_kernel_render_perspective.h:

Program Listing for File perspective.h
======================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_render_perspective.h>` (``ngind/kernel/render/perspective.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #ifndef NGIND_PERSPECTIVE_H
   #define NGIND_PERSPECTIVE_H
   
   #include "math/vector.h"
   #include "include/glm/glm.hpp"
   
   namespace ngind {
   
   class Perspective {
   public:
       static Perspective* getInstance();
   
       static void destroyInstance();
   
       Perspective(const Perspective&) = delete;
       Perspective& operator= (const Perspective&) = delete;
   
       void init(const Vector2D&, const size_t&, const size_t&);
   
       inline void moveTo(const Vector2D& center) {
           init(center, _width, _height);
       }
   
       inline glm::mat4 getProjection() const {
           return _projection;
       }
   
       inline Vector2D getPerspectiveSize() const {
           return Vector2D{_width, _height};
       }
   private:
       Perspective();
   
       ~Perspective() = default;
   
       static Perspective* _instance;
   
       size_t _width, _height;
   
       glm::mat4 _projection;
   };
   
   } // namespace
   
   #endif //NGIND_PERSPECTIVE_H
