#
# Copyright (C) 2018 by Author: Aroudj, Samir
# TU Darmstadt - Graphics, Capture and Massively Parallel Computing
# All rights reserved.
#
# This software may be modified and distributed under the terms
# of the BSD 3-Clause license. See the License.txt file for details.
#

# SurfaceReconstruction library
set(libName SurfaceReconstruction)

# define short aliases for paths
set(componentPath ${PROJECT_SOURCE_DIR}/${libName})
set(imagePath ${componentPath}/Image)
set(geometryPath ${componentPath}/Geometry)
set(refinementPath ${componentPath}/Refinement)
set(renderingPath ${componentPath}/Rendering)
set(scenePath ${componentPath}/Scene)
set(sceneCameraPath ${scenePath}/Camera)
set(sceneTreePath ${scenePath}/Tree)
set(surfaceExtractionPath ${componentPath}/SurfaceExtraction)


#include OpenGL, glut and glew headers
include(${BASE_PROJECT_DIR}/CMake/OpenGL.h.cmake)

# CMake files
set(cmakeFiles
	${componentPath}/CMakeLists.txt
)

# header files

# geometry sub namespace header files
set(geometryHeaderFiles
	${geometryPath}/Edge.h
	${geometryPath}/FlexibleMesh.h
	${geometryPath}/IFlexibleMeshObserver.h
	${geometryPath}/IRayTracerObserver.h
	${geometryPath}/IslesEraser.h	
	${geometryPath}/IVertexChecker.h
	${geometryPath}/Mesh.h		
	${geometryPath}/RayTracer.h
	${geometryPath}/Surfel.h
	${geometryPath}/StaticMesh.h		
	${geometryPath}/Triangle.h
	${geometryPath}/Vertex.h
)

# image sub namespace header files
set(imageHeaderFiles
	${imagePath}/ColorImage.h
	${imagePath}/DepthImage.h
	${imagePath}/ViewsImage.h
	${imagePath}/Filter.h
	${imagePath}/Image.h
	${imagePath}/MVEIHeader.h
)

# refinement sub namespace header files
set(refinementHeaderFiles
	${refinementPath}/FSSFParameters.h
	${refinementPath}/FSSFRefiner.h
	${refinementPath}/FSSFStatistics.h
	${refinementPath}/MeshDijkstra.h
	${refinementPath}/MeshDijkstraParameters.h
	${refinementPath}/MeshRefiner.h
	${refinementPath}/RangedVertexIdx.h
)

# add optional refinement header files
if (PCS_REFINEMENT)
	set(refinementHeaderFiles 
		${refinementHeaderFiles}
		${refinementPath}/PatchStatistics.h
		${refinementPath}/PCSRefiner.h
	)
endif (PCS_REFINEMENT)

# rendering sub namespace header files
set(renderingHeaderFiles
	${renderingPath}/MeshRenderer.h
	${renderingPath}/Renderer.h	
)

# scene sub namespace header files
set(sceneHeaderFiles
	${scenePath}/CapturedScene.h
	${scenePath}/FileNaming.h
	${scenePath}/IReconstructorObserver.h
	${scenePath}/Samples.h
	${scenePath}/Scene.h
	${scenePath}/SyntheticScene.h
)

# Scene/Camera sub namespace header files
set (sceneCameraHeaderFiles
	${sceneCameraPath}/Cameras.h
	${sceneCameraPath}/CameraData.h
	${sceneCameraPath}/MVECameraIO.h
)

# scene/tree sub namespace header files
set (sceneTreeHeaderFiles
	${sceneTreePath}/DualCells.h
	${sceneTreePath}/NodesChecker.h
	${sceneTreePath}/Leaves.h
	${sceneTreePath}/LeavesIterator.h
	${sceneTreePath}/Nodes.h
	${sceneTreePath}/NodesIterator.h
	${sceneTreePath}/Scope.h
	${sceneTreePath}/SphereNodesChecker.h
	${sceneTreePath}/Tree.h
	${sceneTreePath}/TriangleNodesChecker.h
)

# surface extraction sub namespace header files
set(surfaceExtractionHeaderFiles
	${surfaceExtractionPath}/ConeNodesChecker.h
	${surfaceExtractionPath}/DualMarchingCell.h
	${surfaceExtractionPath}/DualMarchingCells.h
	${surfaceExtractionPath}/EdgeVertexIndex.h
	${surfaceExtractionPath}/LineChecker.h
	${surfaceExtractionPath}/Occupancy.h
	${surfaceExtractionPath}/SphereNodeStatesChecker.h
)

# source files

# geometry sub namespace source files
set(geometrySourceFiles
	${geometryPath}/Edge.cpp
	${geometryPath}/FlexibleMesh.cpp
	${geometryPath}/IslesEraser.cpp
	${geometryPath}/StaticMesh.cpp		
	${geometryPath}/Mesh.cpp	
	${geometryPath}/RayTracer.cpp	
	${geometryPath}/Surfel.cpp
	${geometryPath}/Triangle.cpp
	${geometryPath}/Vertex.cpp
)

# image sub namespace source files
set(imageSourceFiles
	${imagePath}/ColorImage.cpp
	${imagePath}/DepthImage.cpp
	${imagePath}/ViewsImage.cpp
	${imagePath}/Filter.cpp
	${imagePath}/Image.cpp
	${imagePath}/MVEIHeader.cpp
)

# refinement sub namespace source files
set(refinementSourceFiles
	${refinementPath}/FSSFParameters.cpp
	${refinementPath}/FSSFRefiner.cpp
	${refinementPath}/FSSFStatistics.cpp
	${refinementPath}/MeshDijkstra.cpp
	${refinementPath}/MeshDijkstraParameters.cpp
	${refinementPath}/MeshRefiner.cpp
	${refinementPath}/RangedVertexIdx.cpp
)

# add optional refinement source files
if (PCS_REFINEMENT)
	set(refinementSourceFiles
		${refinementSourceFiles}
		${refinementPath}/PatchStatistics.cpp
		${refinementPath}/PCSRefiner.cpp
	)
endif (PCS_REFINEMENT)

# rendering sub namespace source files
set(renderingSourceFiles
	${renderingPath}/MeshRenderer.cpp
	${renderingPath}/Renderer.cpp	
)

# scene sub namespace source files
set(sceneSourceFiles
	${scenePath}/CapturedScene.cpp
	${scenePath}/FileNaming.cpp
	${scenePath}/Samples.cpp
	${scenePath}/Scene.cpp
	${scenePath}/SyntheticScene.cpp
)

# Scene/Camera sub namespace ource files
set (sceneCameraSourceFiles
	${sceneCameraPath}/Cameras.cpp
	${sceneCameraPath}/CameraData.cpp
	${sceneCameraPath}/MVECameraIO.cpp
)

# scene/tree sub namespace source files
set (sceneTreeSourceFiles
	${sceneTreePath}/DualCells.cpp
	${sceneTreePath}/Leaves.cpp
	${sceneTreePath}/LeavesIterator.cpp
	${sceneTreePath}/Nodes.cpp
	${sceneTreePath}/NodesIterator.cpp
	${sceneTreePath}/Scope.cpp
	${sceneTreePath}/SphereNodesChecker.cpp
	${sceneTreePath}/Tree.cpp
	${sceneTreePath}/TriangleNodesChecker.cpp
)

# surface extraction sub namespace source files
set(surfaceExtractionSourceFiles	
	${surfaceExtractionPath}/ConeNodesChecker.cpp
	${surfaceExtractionPath}/DualMarchingCell.cpp
	${surfaceExtractionPath}/DualMarchingCells.cpp	
	${surfaceExtractionPath}/DualMarchingCellTables.cpp
	${surfaceExtractionPath}/EdgeVertexIndex.cpp
	${surfaceExtractionPath}/LineChecker.cpp
	${surfaceExtractionPath}/Occupancy.cpp
	${surfaceExtractionPath}/SphereNodeStatesChecker.cpp
)

# gather all header files in headerFiles
set(headerFiles
	${imageHeaderFiles}
	${geometryHeaderFiles}
	${refinementHeaderFiles}
	${renderingHeaderFiles}
	${sceneHeaderFiles}
	${sceneTreeHeaderFiles}
	${sceneCameraHeaderFiles}
	${surfaceExtractionHeaderFiles}
)

# gather all source files in sourceFiles
set(sourceFiles
	${imageSourceFiles}
	${geometrySourceFiles}
	${refinementSourceFiles}
	${renderingSourceFiles}
	${sceneSourceFiles}
	${sceneCameraSourceFiles}
	${sceneTreeSourceFiles}
	${surfaceExtractionSourceFiles}
)

# get all file groups together
set(libFiles
	${cmakeFiles}
	${headerFiles}
	${sourceFiles}
)

add_library(${libName} ${libFiles})

# define source groups for file management within IDE
source_group("CMake" FILES ${cmakeFiles})
source_group("Geometry" FILES ${geometryHeaderFiles} ${geometrySourceFiles})
source_group("Image" FILES ${imageHeaderFiles} ${imageSourceFiles})
source_group("Refinement" FILES ${refinementHeaderFiles} ${refinementSourceFiles})
source_group("Rendering" FILES ${renderingHeaderFiles} ${renderingSourceFiles})
source_group("Scene" FILES ${sceneHeaderFiles} ${sceneSourceFiles})
source_group("Scene\\Camera" FILES ${sceneCameraHeaderFiles} ${sceneCameraSourceFiles})
source_group("Scene\\Tree" FILES ${sceneTreeHeaderFiles} ${sceneTreeSourceFiles})
source_group("SurfaceExtraction" FILES ${surfaceExtractionHeaderFiles} ${surfaceExtractionSourceFiles})
