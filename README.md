# GLSLValidateVS

This property page for Visual Studio allows GLSL shader files to be sent to glslValidator upon build time.


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
* Viola! From this point forward, any shader files you add to your project will checked upon build time. The following extensions are supported:
** .frag
** .vert
** .geom
** .comp
** .tese
** .tesc
* If you don't like this and would prefer to set your shader files up manually (see below), check out GLSLValidateTargets.props for instructions on how to disable this behavior.

## Manually setting shader files to be checked
If you have existing shader files in your project, they won't automatically be set up to be validated at build time. You'll have to set their item type yourself. To do this:
* Select your shader files in your project
* Right click on them and go to properties
* In the dialog that opens, Select the General category
* Select GLSL Validator from the Item Type dropdown.

[GLSL Reference compiler page at khronos] https://www.khronos.org/opengles/sdk/tools/Reference-Compiler/
[Download the glslangValidator executable] https://cvs.khronos.org/svn/repos/ogl/trunk/ecosystem/public/sdk/tools/glslang/Install/
