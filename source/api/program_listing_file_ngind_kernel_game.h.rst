
.. _program_listing_file_ngind_kernel_game.h:

Program Listing for File game.h
===============================

|exhale_lsh| :ref:`Return to documentation for file <file_ngind_kernel_game.h>` (``ngind/kernel/game.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   
   #ifndef NGIND_GAME_H
   #define NGIND_GAME_H
   
   #include <map>
   #include <string>
   #include <stack>
   
   #include "resources/config_resource.h"
   #include "timer/timer.h"
   #include "objects/world.h"
   
   namespace ngind {
   
   class Game {
   public:
       static Game* getInstance();
   
       static void destroyInstance();
   
       void loadWorld(const std::string&);
   
       void destroyWorld(const std::string&);
   
       void pushAndLoadWorld(const std::string&);
   
       void popAndLoadWorld(const bool&);
   
       void DestroyAndLoadWorld(const std::string&);
   
       void start();
   
       inline World* getCurrentWorld() {
           return _current_world;
       }
   
       inline void quit() {
           this->_loop_flag = false;
       }
   
   private:
       Game();
   
       ~Game();
   
       static Game* _instance;
   
       ConfigResource* _global_settings;
   
       Timer _global_timer;
   
       World* _current_world;
   
       std::map<std::string, World*> _worlds;
   
       std::stack<World*> _stack;
   
       bool _loop_flag;
   };
   
   } // namespace ngind
   
   #endif //NGIND_GAME_H
