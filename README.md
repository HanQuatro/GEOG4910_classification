# Create a search cursor that converts geometries to the WGS84 SRS
with arcpy.da.SearchCursor(
    in_table='sites.shp', field_names=['shape@x', 'shape@y'], spatial_reference=srs) as searcher:
    
    # Loop through the rows and print them out
    for row in searcher:
      print(row)
# Create a search cursor that gets the geometry objects
with arcpy.da.SearchCursor(in_table = 'sites.shp', field_names = 'shape@') as searcher:
    
    # Get the first row (next() gets the next row in line)
    row = next(searcher)
    
    # Get the geometry (it's the only thing in the row's tuple and has index 0)
    geom = row[0]
    
    # Print out the geometry's spatial reference name
    print(geom.spatialReference.name)
