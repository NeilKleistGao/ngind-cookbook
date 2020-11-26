
.. _program_listing_file_ngind_kernel_math_vector.h:

Program Listing for File vector.h
=================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_math_vector.h>` (``ngind/kernel/math/vector.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_VECTOR_H
   #define NGIND_VECTOR_H
   
   #include <cmath>
   
   namespace ngind {
   
   class Vector2D {
   public:
   
       Vector2D();
   
       Vector2D(const float&, const float&);
   
       Vector2D(const Vector2D&);
   
       inline float getX() const {
           return _x;
       }
   
       inline float getY() const {
           return _y;
       }
   
       inline void setX(const float& x) {
           this->_x = x;
       }
   
       inline void setY(const float& y) {
           this->_y = y;
       }
   
       Vector2D operator* (const float&) const;
   
       Vector2D& operator*= (const float&);
   
       Vector2D operator+ (const Vector2D&) const;
   
       Vector2D& operator+= (const Vector2D&);
   
       Vector2D operator- (const Vector2D&) const;
   
       Vector2D& operator-= (const Vector2D&);
   
       bool operator== (const Vector2D&) const;
   
       bool operator!= (const Vector2D&) const;
   
       Vector2D& operator= (const Vector2D&);
   
       float operator* (const Vector2D&) const;
   
       float getMagnitude() const;
   
       float getMagnitude2() const;
   
       Vector2D normalize() const;
   
       Vector2D getNormalOrthogonalVector() const;
   
       Vector2D project(const Vector2D&) const;
   
       float getAngle(const Vector2D&) const;
   
       bool isCollinear(const Vector2D&) const;
   
       bool isReverse(const Vector2D&) const;
   
       bool isOrthogonal(const Vector2D&) const;
   
       static const Vector2D INVALID, ORIGIN;
   
       inline bool isValid() const {
           return !std::isnan(_x) && !std::isnan(_y);
       }
   
       inline float cross(const Vector2D& v) const {
           return _x * v._y - _y * v._x;
       }
   
   private:
       constexpr static float EPSILON = 1e-6;
   
       float _x, _y;
   };
   
   inline Vector2D operator* (const float& s, const Vector2D& v) {
       return v * s;
   }
   
   } // namespace ngind
   
   #endif //NGIND_VECTOR_H
