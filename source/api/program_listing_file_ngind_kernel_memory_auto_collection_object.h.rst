
.. _program_listing_file_ngind_kernel_memory_auto_collection_object.h:

Program Listing for File auto_collection_object.h
=================================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_memory_auto_collection_object.h>` (``ngind/kernel/memory/auto_collection_object.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_AUTO_COLLECTION_OBJECT_H
   #define NGIND_AUTO_COLLECTION_OBJECT_H
   
   namespace ngind {
   class AutoCollectionObject {
   public:
       AutoCollectionObject();
   
       virtual ~AutoCollectionObject() = default;
   
       inline void addReference() {
           // CALL ME MOMMY
           // JUST LIKE YOUR FANTASY
           // There is no crime in ideality
           // MUX>>>DEMUX
           // Can't you understand me?
           // I'm not mine NAND I'm not yours
           this->_sustain++;
       }
   
       void removeReference();
   
       inline short getSustain() const {
           return this->_sustain;
       }
   
   private:
       short _sustain;
   };
   } // namespace ngind
   
   #endif //NGIND_AUTO_COLLECTION_OBJECT_H
