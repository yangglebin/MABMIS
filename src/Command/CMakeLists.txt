# build your own project
PROJECT(IterativeGroupwiseRegistration3D)

CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

# Find ITK
FIND_PACKAGE(ITK)
IF(ITK_FOUND)
	INCLUDE(${ITK_USE_FILE})
ELSE(ITK_FOUND)
	MESSAGE(FATAL_ERROR
		"ITK not found.  Please set ITK_DIR.")
ENDIF(ITK_FOUND)


ADD_EXECUTABLE(IGR3D_MABMIS_i IGR3D_MABMIS_i.cxx itkJia3D.cxx itkJia3D.h )
TARGET_LINK_LIBRARIES(IGR3D_MABMIS_i ITKIO ITKCommon ITKStatistics ITKNumerics)

ADD_EXECUTABLE(NormalizeIntensity normalize_intensity.cc itkJia3D.cxx itkJia3D.h)
TARGET_LINK_LIBRARIES(NormalizeIntensity ITKCommon ITKIO ITKNumerics ITKStatistics)

ADD_EXECUTABLE(ApplyDeformationField apply_deformation_field.cc itkJia3D.cxx itkJia3D.h)
TARGET_LINK_LIBRARIES(ApplyDeformationField ITKCommon ITKIO ITKNumerics ITKStatistics)


