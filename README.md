Shaperead2.m
===================

SHAPEREAD2: Reads a shapefile into MATLAB m-file and apply the projection if possible

This code was created as a GEOG790 Project at Northern Illinois University Geography Department in Fall 2012 by Grant Herbert. 

 SHAPEREAD2 is a Wrapper for shaperead() and accepts the same parameters.
 It returns a map mstruct array and then the same outputs as shaperead.
 *The mstruct output is required*.
 Parts of the shaperead documentation are repeated here for consistency,
 see the shaperead MATLAB documentation for details.
 
 SHAPEREAD2 looks for a shapefile projection file (.prj), reads in the WKT 
 value, parses the name and uses it to get the MATLAB projection parameters
 from the mapping toolbox 'esri' file (parameters are actually proj4 
 but they work for this purpose). If no projection file exists, or no 
 projection parameters are found then the returned mstruct will be empty.

 [mstruct S] = shaperead2(FILENAME) returns a projection mstruct and a
 N-by-1 structure array, S, containing one element for each non-null 
 geographic feature in the shapefile.

 [mstruct S A] = shaperead2(FILENAME) returns a projection mstruct and a 
 N-by-1 structure array, S, containing one element for each non-null 
 geographic feature, omitting any non-spatial attributes, and a 
 parallel N-by-1 attribute structure array, A.

 [mstruct S] = shaperead2(FILENAME,PARAM1,VAL1,PARAM2,VAL2,...) returns a
 projection mstruct and a subset of the shapefile contents in S, as 
 determined by the parameters 'RecordNumbers','BoundingBox','Selector', 
 or 'Attributes'. S is a mapstruct unless the parameter 'UseGeoCoords' 
 is provided with a value of true.  In that case, the X and Y-coordinates 
 within the shapefile are interpreted as longitudes and latitudes, 
 respectively, and S is a "geostruct" with 'Lat' and 'Lon' fields rather 
 than 'X' and 'Y' fields.

 REQUIRED ARG IN: filename
 OPTIONAL ARGS IN: same as shaperead() 
 REQUIRED ARGS OUT: mstruct of projection parameters, S
 OPTIONAL ARG OUT: A