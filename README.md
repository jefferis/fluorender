FluoRender
========

FluoRender2.14 Release Source Code

This is the open-source repository for FluoRender2.14, an interactive rendering tool for confocal microscopy data visualization. It combines the renderings of multi-channel volume data and polygon mesh data, where the properties of each dataset can be adjusted independently and quickly. The tool is designed especially for neurobiologists, and it helps them better visualize the fluorescent-stained confocal samples.

Aknowledgements
========
If you use FluoRender in work that leads to published research, we humbly ask that you add the following to the 'Acknowledgments' section of your paper: 
"This work was made possible in part by software funded by the NIH: Fluorender: An Imaging Tool for Visualization and Analysis of Confocal Data as Applied to Zebrafish Research, R01-GM098151-01."

<strong>Author: </strong> Yong Wan<br/>
<strong>Developer: </strong> Brig Bagley<br/>

Building FluoRender
========
Requirements: Git, CMake, wxWidgets 3.0<br/>
We recommend building FluoRender outside of the source tree. <br/>

<h4>OSX</h4> 

1) Download and install "Homebrew", found at "http://brew.sh"

2) Install WxWidgets using Homebrew.

   * Type <code>brew edit wxmac</code> and change <code>--enable-shared</code> to <code>--disable-shared</code><br/>
  
   * Type <code>brew install --build-from-source --devel wxwidgets</code><br/>

   * You may need root pivileges to link the libraries if brew asks you to.<br/>

3) In the main FluoRender directory, (containing "CMakeLists.txt" & "fluorender" folder):
   
   * <code>mkdir build</code><br/>
   
   * <code>cd build</code><br/>

   * <code>cmake ..</code><br/>

   * <code>ccmake ..</code> (To configure build properties)<br/>

   * <code>make</code><br/><br/>

4) Using cmake, you can generate XCode (MacOS X). Simply type "cmake" to find the proper options.

   * <code>cmake -G Xcode</code><br/>

   * You may need to clear old cmake files. Type <code>./clear.sh</code> to remove unneccessary files.<br/> 

--------------------------------------------------------------------------------------------------
Windows Installation
--------------------------------------------------------------------------------------------------

1) Download the latest wxWidgets (currently 3.0.0).

2) Install the headers and libraries to your system.

    * Download and install using the installer. 

    * Compile using Visual Studio (C:/wxWidgets-3.0.0/build/msw/wx_vc7.sln)

    * Be sure to compile the same configuration (Debug/Release) as you do for FluoRender below.

2) You will need to add lines to C:/Program Files (x86)/CMake X.X/share/cmake-x.x/Modules (x's are your version) 
    for wxWidgets 3.0.

    * Starting about line 277, you will have listed a few sets of library versions to 
     search for like "wxbase29${_UCD}${_DBG}"

    * In 4 places, you will need to add above each line with a "29" a new line that is exactly the same, but with a "30" instead.

3) In the main FluoRender directory, (containing "CMakeLists.txt" & "fluorender" folder):

    * Use the C:\Program Files(x86)\CMake2.8\bin\cmake-gui.exe in the CMake install folder to configure build properties.

         - Choose the FluoRender main folder for both browse options (source and build)

         - Edit the values as necessary, Click Configure, then Click Generate.
              Be sure to set wxWidgets_LIB_DIR to C:/wxWidgets-3.0.0/lib/vc_lib 
			                                     (C:/wxWidgets-3.0.0/lib/vc_x64_lib for 64 bit)
              Be sure to set wxWidgets_ROOT_DIR to C:/wxWidgets-3.0.0 (assuming these are your wxWidget dirs)

    * If all properties are set as desired, type "cmake ." in the terminal. 

	     - To specify 32/64 bit or Visual Studio versions for making the solution file, type "cmake --help" for options.

		 - Example: "cmake -G "Visual Studio 10 Win64"

    * Open the Visual Studio SLN file generated by CMake.

    * Build the solution.
	   
	     - Visual Studio may not set the correct machine target when building 64 bit.
		   Check Project Properties -> Configuration Properties -> Linker -> Command line.
		   Make sure "Additional Options" should is "/machine:X64" NOT "/machine:X86"

         - You may need to right-click FluoRender project on the left to "Set as StarUp Project" for it to run.

         - You may also need to add additional dependencies in the FluoRender properties.
    
    * NOTE: There are known issues with rendering XML stitched TIFF files when in "Debug" Configuration.


--------------------------------------------------------------------------------------------------

If there are any problems, email: fluorender@sci.utah.edu
