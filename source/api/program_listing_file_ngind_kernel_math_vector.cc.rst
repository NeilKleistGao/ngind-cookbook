
.. _program_listing_file_ngind_kernel_math_vector.cc:

Program Listing for File vector.cc
==================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_math_vector.cc>` (``ngind/kernel/math/vector.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   
   #include "vector.h"
   
   namespace ngind {
   const Vector2D Vector2D::INVALID = Vector2D{NAN, NAN};
   const Vector2D Vector2D::ORIGIN = Vector2D{0, 0};
   
   Vector2D::Vector2D() : Vector2D(0.0f, 0.0f) {
   }
   
   Vector2D::Vector2D(const float& x, const float& y) : _x(x), _y(y) {
   }
   
   Vector2D::Vector2D(const Vector2D& v) : Vector2D(v.getX(), v.getY()) {
   }
   
   Vector2D Vector2D::operator* (const float& s) const {
       auto vec = *this;
       vec *= s;
       return vec;
   }
   
   Vector2D& Vector2D::operator*= (const float& s) {
       this->_x *= s;
       this->_y *= s;
       return *this;
   }
   
   Vector2D Vector2D::operator+ (const Vector2D& v) const {
       auto vec = *this;
       vec += v;
       return vec;
   }
   
   Vector2D& Vector2D::operator+= (const Vector2D& v) {
       this->_x += v._x;
       this->_y += v._y;
       return *this;
   }
   
   Vector2D Vector2D::operator- (const Vector2D& v) const {
       Vector2D vec = *this;
       vec -= v;
       return vec;
   }
   
   Vector2D& Vector2D::operator-= (const Vector2D& v) {
       this->_x -= v._x;
       this->_y -= v._y;
       return *this;
   }
   
   bool Vector2D::operator== (const Vector2D& v) const {
       return this->_x == v._x && this->_y == v._y;
   }
   
   bool Vector2D::operator!= (const Vector2D& v) const {
       return !((*this) == v);
   }
   
   Vector2D& Vector2D::operator= (const Vector2D& v) {
       this->_x = v._x;
       this->_y = v._y;
       return *this;
   }
   
   float Vector2D::operator* (const Vector2D& v) const {
       return this->_x * v._x + this->_y * v._y;
   }
   
   float Vector2D::getMagnitude() const {
       return std::sqrt(this->getMagnitude2());
   }
   
   float Vector2D::getMagnitude2() const {
       float x2 = this->_x * this->_x,
               y2 = this->_y * this->_y;
       return x2 + y2;
   }
   
   Vector2D Vector2D::normalize() const {
       float mag = this->getMagnitude();
       Vector2D vec = *this;
       vec *= (1.0f / mag);
       return vec;
   }
   
   Vector2D Vector2D::getNormalOrthogonalVector() const {
       return Vector2D(this->_y, -this->_x).normalize();
   }
   
   Vector2D Vector2D::project(const Vector2D& v) const {
       Vector2D norm = v.normalize();
       float pro = (*this) * v;
       float cos_pro = pro / (this->getMagnitude() * v.getMagnitude());
       float len = this->getMagnitude() * cos_pro;
       return len * norm;
   }
   
   float Vector2D::getAngle(const Vector2D& v) const {
       float pro = (*this) * v;
       pro /= (this->getMagnitude() * v.getMagnitude());
       return std::acos(pro);
   }
   
   bool Vector2D::isCollinear(const Vector2D& v) const {
       float mag1 = this->getMagnitude2(),
             mag2 = v.getMagnitude2();
       return std::abs(mag1 * mag2 - (*this) * v) < EPSILON;
   }
   
   bool Vector2D::isReverse(const Vector2D& v) const {
       float mag1 = this->getMagnitude2(),
               mag2 = v.getMagnitude2();
       return mag1 * mag2 - (*this) * v < 0;
   }
   
   bool Vector2D::isOrthogonal(const Vector2D& v) const {
       return std::abs((*this) * v) < EPSILON;
   }
   
   } // namespace ngind
