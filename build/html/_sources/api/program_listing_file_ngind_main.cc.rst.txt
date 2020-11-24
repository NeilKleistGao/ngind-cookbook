
.. _program_listing_file_ngind_main.cc:

Program Listing for File main.cc
================================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_main.cc>` (``ngind/main.cc``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #include "kernel/game.h"
   
   #include <iostream>
   
   int main() {
       auto game = ngind::Game::getInstance();
       if (game == nullptr) {
           exit(-1);
       }
   
       // Good Luck, Have Fun.
       game->start();
       return 0;
   }
