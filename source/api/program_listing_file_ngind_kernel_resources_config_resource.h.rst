
.. _program_listing_file_ngind_kernel_resources_config_resource.h:

Program Listing for File config_resource.h
==========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_config_resource.h>` (``ngind/kernel/resources/config_resource.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: config_resource.h
   // LAST MODIFY: 2020/10/11
   
   #ifndef NGIND_CONFIG_RESOURCE_H
   #define NGIND_CONFIG_RESOURCE_H
   
   #include "resource.h"
   
   #include "include/rapidjson/document.h"
   
   namespace ngind {
   
   class ConfigResource : public Resource {
   public:
       const static std::string CONFIG_RESOURCE_PATH;
   
       ConfigResource() = default;
       ~ConfigResource() override = default;
       virtual void load(const std::string&);
   
       using JsonObject = rapidjson::GenericValue<rapidjson::UTF8<>>;
   
       inline rapidjson::Document& getDocument() {
           return _doc;
       }
   private:
       rapidjson::Document _doc;
   };
   
   }
   
   #endif //NGIND_CONFIG_RESOURCE_H
