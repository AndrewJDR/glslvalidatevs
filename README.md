# GLSLValidateVS

This property page for Visual Studio allows GLSL shader files to be sent to glslValidator upon build time. If shader syntax errors are found, they'll be printed to the Build Output window and the build will fail.

Another benefit of using this is that your project will be built if a shader file gets updated. Typically, shader files don't participate in the build at all, and thus updating them will not cause your project to build when you hit F7 or the like. This can be important if you have post-build steps that need to run when any of your project files are updated (e.g. a post build step that copies your shader files into a deployment directory).

## Prerequisites
[Download the glslangValidator executable] and find a home for it on your drive. Visit the [GLSL Reference compiler page at khronos] for more information on that project.

## Usage
* Put the two .props files somewhere on your drive
* With your project open Visual Studio, go to the property manager (View > Property Manager)
* Right click on your project in the Property Manager and choose "Add existing Property Sheet"
* Select the GLSLValidateVS.props file
* If you expand any of the configurations under your project (e.g. Debug|x64, Release|x64, etc), you should now notice a GLSLValidateVS item. Right click on it and go to properties.
* In the properties dialog that opens, navigate to the "User Macros" category
* Set GLSLVALIDATOREXE to the path to your glslangValidator executable (You can alternatively set a system-wide GLSLVALIDATOREXE environment variable)
* You may need to restart Visual Studio and reopen your project
* Voila! From this point forward, files you add to your project (with the following file extensions) will sent to  glslangValidator upon build time. Any errors will be printed to the Build Output window in Visual Studio. Note, only files with the following extensions are supported by glslangValidator:
  * .frag
  * .vert
  * .geom
  * .comp
  * .tese
  * .tesc
* If you would prefer to manually define which files in your project get checked, see the instructions below and also check out GLSLValidateTargets.props on how to disable the automatic file extension based item type setting.

## Manually setting shader files to be checked
If you have existing shader files in your project, they won't automatically be set up to be validated at build time. You'll have to set their item type yourself. To do this:
* Select your shader files in your project
* Right click on them and go to properties
* In the dialog that opens, Select the General category
* Select GLSL Validator from the Item Type dropdown.
* The file(s) will now be checked by glslangValidator upon build time. Note, glslangValidator appears to use the file extension (supported extensions listed above) to determine how to parse the file, so you'll probably need appropriate file extensions on your shader files for this to work.

[GLSL Reference compiler page at khronos]: https://www.khronos.org/opengles/sdk/tools/Reference-Compiler/
[Download the glslangValidator executable]: https://cvs.khronos.org/svn/repos/ogl/trunk/ecosystem/public/sdk/tools/glslang/Install/
