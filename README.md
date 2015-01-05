FluoRender
========

FluoRender Source Code

This is the open-source repository for FluoRender, an interactive rendering tool for confocal microscopy data visualization. It combines the renderings of multi-channel volume data and polygon mesh data, where the properties of each dataset can be adjusted independently and quickly. The tool is designed especially for neurobiologists, and it helps them better visualize the fluorescent-stained confocal samples.

Aknowledgements
========
If you use FluoRender in work that leads to published research, we humbly ask that you add the following to the 'Acknowledgments' section of your paper: 
"This work was made possible in part by software funded by the NIH: Fluorender: An Imaging Tool for Visualization and Analysis of Confocal Data as Applied to Zebrafish Research, R01-GM098151-01."

<strong>Author: </strong> Yong Wan<br/>
<strong>Developer: </strong> Brig Bagley<br/>

Building FluoRender
========
Requirements: Git, CMake, wxWidgets 3.*, boost<br/>
We recommend building FluoRender outside of the source tree. <br/>

<h4>OSX</h4> 

1) Download and install "Homebrew", found at "http://brew.sh"

2) Install WxWidgets using Homebrew on the command line.

   * Type <code>brew edit wxmac</code> and change <code>--enable-shared</code> to <code>--disable-shared</code><br/>
  
   * Type <code>brew install --build-from-source --devel wxwidgets</code><br/>

   * You may need root pivileges to link the libraries if brew asks you to.<br/>
   
   * Note the location of the wxWidget directories for ccmake.

   * If you choose to build from source, a working configuration call is : <code>../configure --disable-shared --enable-macosx_arch=x86_64 --enable-unicode --with-osx_cocoa --enable-debug</code> In ccmake, you can set the <code>wxrc</code> and <code>wx-config</code> executables generated from the source build.

3) Download and include boost.

   * Download boost(http://www.boost.org/users/download/#live) and extract onto your machine.
   
   * Note the location of the boost include directory for ccmake.

4) In the main FluoRender directory, (containing "CMakeLists.txt" & "fluorender" folder):
   
   * <code>mkdir build</code><br/>
   
   * <code>cd build</code><br/>

   * <code>cmake ..</code><br/>

   * <code>ccmake ..</code> (To configure build properties such as wxWidgets and Boost locations)<br/>

   * <code>make</code><br/><br/>

5) Using cmake, you can generate XCode (MacOS X). Simply type "cmake" to find the proper options.

   * <code>cmake -G Xcode</code><br/>

   * You may need to clear old cmake files. Type <code>./clear.sh</code> to remove unneccessary files.<br/> 

<h4>Windows</h4> 

1) Download the latest wxWidgets (currently 3.* at http://www.wxwidgets.org/).

2) Install the headers and libraries to your system.

   * Download and install using the installer.<br/> 
  
   * Compile using Visual Studio (EG Solution file: "C:/wxWidgets-3.0.2/build/msw/wx_vc7.sln")<br/> 

   * Be sure to compile the same configurations (Debug/Release/64bit) you will use for FluoRender below.<br/> 
   
   * Note the location of the appropriate wxWidget directories for cmake configuration.
   
3) Download and include boost.

   * Download boost(http://www.boost.org/users/download/#live) and extract onto your machine.
   
   * Note the location of the boost include directory for cmake.

4) You may need to add lines to C:/Program Files (x86)/CMake X.X/share/cmake-x.x/Modules/FindwxWidgets.cmake (x's are your version) for wxWidgets 3.0 if it still complains that you haven't installed wxWidgets.
   
   * Starting about line 277, you will have listed a few sets of library versions to search for like "wxbase29${_UCD}${_DBG}" <br/>
   
   * In 4 places, you will need to add above each line with a "29" a new line that is exactly the same, but with a "30" instead, assuming your version of wxWidgets is 3.0.*). <br/>

5) In the main FluoRender directory, (containing "CMakeLists.txt" & "fluorender" folder):

   * Use the C:\Program Files(x86)\CMake2.8\bin\cmake-gui.exe in the CMake install folder to configure build properties. This is where you will add the locations of boost and wxWidgets directories after generation and before configuration. You may need to display advanced options. <br/>
   	- Choose the FluoRender main folder for source and create a new folder for the build. <br/>

   	- Click Configure, Edit the values as necessary, then Click Configure & Generate. Be sure to set wxWidgets_LIB_DIR to C:/wxWidgets-3.0.2/lib/vc_x64_lib. Be sure to set wxWidgets_ROOT_DIR to C:/wxWidgets-3.0.2 (assuming these are your wxWidget dirs) and Boost_INCLUDE_DIR to C:/boost_1_55_0 (assuming this is your boost dir). <br/>

   * You may also generate using the command prompt, but you must explicitly type the paths for the cmake command. <br/>
   
    - Open Visual Studio 2010 64 bit Command Prompt. Go to the CMakeLists.txt directory. <br/>
    	
    - Type <code> cmake -G "Visual Studio 10 Win64" -DwxWidgets_LIB_DIR="C:/wxWidgets-3.0.2/lib/vc_x64_lib" -DwxWidgets_ROOT_DIR="C:/wxWidgets-3.0.2" -DBoost_INCLUDE_DIR="C:/boost_1_55_0" ..</code> in your build directory (again assuming these are your directory locations). <br/>
    	
   * Open the Visual Studio SLN file generated by CMake (found in your "build" directory). <br/>
   
   * Build the solution.<br/>
    	
    - Visual Studio may not set the correct machine target when building 64 bit. Check Project Properties -> Configuration Properties -> Linker -> Command line. Make sure "Additional Options" should is "/machine:X64" NOT "/machine:X86". <br/>
    	
    - You may need to right-click FluoRender project on the left to "Set as StarUp Project" for it to run. <br/>

Contact
========

If there are any problems, email: fluorender@sci.utah.edu
