# GDExtension Example Project
Example project with Godot4 and GDExtension

This project shows an example of how to set up and install plugins in godot4 alpha

## Set up

1. Download or clone repo
2. go to godot-cpp-master folder and build cpp bindings
 
        cd godot-cpp-master
  
        scons target=debug
 
3. go to example_plugin folder and build plugin WITH ADMIN PRIVILEGES (it is unclear to me why but libgdexample.linux.debug.x86_64.so will prevent your build if you don't use admin privileges) 
           
        cd plugins/example_plugin
        
        sudo scons target=debug

4. Import project

### Alternatively copy godot-cpp-master and plugins folder into your own project and build them there.

If you decide to mess with the folder structure, make sure to update:

1. plugins/example_plugin/SConstruct

      env = SConscript("relative_path_to_your_godot-cpp-master/Sconstruct") 

2. plugins/example_plugin/CMakeLists.txt

       set(GODOT_HEADERS_PATH "relative_path_to_your_godot-headers_folder" CACHE STRING "Path to Godot headers")
       set(CPP_BINDINGS_PATH "relative_path_to_your_godot-cpp-master_folder CACHE STRING "Path to C++ bindings
      
      
 ## Known Issues
 
 1. When compiling the plugin, not using admin privaliges will cause a access prohibited error for libgdexample.linux.debug.x86_64.so
 2. At runtime two errors which are also present in the official example appear (on my machine at lease)
 
         1)  _ready: Condition "_instance_bindings != nullptr" is true.
         2)  set_instance_binding: Condition "_instance_bindings != nullptr" is true.
    
