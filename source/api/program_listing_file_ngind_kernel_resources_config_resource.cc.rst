
.. _program_listing_file_ngind_kernel_resources_config_resource.cc:

Program Listing for File config_resource.cc
===========================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_resources_config_resource.cc>` (``ngind/kernel/resources/config_resource.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   // FILENAME: config_resource.cc
   // LAST MODIFY: 2020/10/30
   
   #include "config_resource.h"
   
   #include "filesystem/file.h"
   
   namespace ngind {
   const std::string ConfigResource::CONFIG_RESOURCE_PATH = "resources/config";
   
   void ConfigResource::load(const std::string& filename) {
       File* fp = new File(CONFIG_RESOURCE_PATH + "/" + filename, "r");
       std::string content = fp->readToEnd();
       fp->close();
   
       _doc.Parse(content.c_str());
       this->_path = filename;
   }
   } // namespace ngind
