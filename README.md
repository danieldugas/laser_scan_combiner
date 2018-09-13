## laser_scan_combiner

A ROS Package to two 2D LiDAR scan into one.

This was created in order to use more than a single scanner in gmapping.

Input:
/scan1: topic for the LaserScan messages published by the first laser.
/scan2_cloud: topic for PointCloud2 messages published by the second laser.

Output:
/combined_scan: A single LaserScan topic, in the frame of the first laser.


Scans are not accumulated.
They are not truly combined in that sense.
Scans get converted into the first laser frame and published immediately,
meaning that subsequent scans in the /combined_scan topic should not be assumed to cover the same space.

The output scan has a higher resolution than the original scan, by a factor of n=3. (currently hardcoded)
No interpolation is performed, points from the second laser are put in the nearest angular 'bin' in the resulting scan frame.

