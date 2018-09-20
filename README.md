# Collision-avoidance-algorithm-for-an-Unmanned-Aerial-Vehicle-cyber-physical-system
As part of my dissertation, I created an algorithm helping a UAV to perform a collission avoidance action in order not to crash with an obstacle whose location is known a priori. The model was written using the modelling language VDM. The simulations were performed using INTO-CPS.

Collision avoidance
As the 20-sim model does not support any kind of sensors, we should find out how to detect
obstacles. Every time the UAV flies to a new waypoint, it checks whether there is an obstacle
between its location and the waypoint’s location. It generates intermediate points from its
position to the next waypoint’s position. Since we know two points, we can determine the

equation of the line that connects the two points, there are three scenarios, and our model
is able to deal with all of them.
If even one of these intermediate points have distance from the obstacle less than a
specified radius, the UAV generates an extra waypoint to avoid the obstacle. The extra
waypoint is generated considering the obstacle’s position to minimize the path.
In this figure, the red circle represents the obstacle. The UAV identifies the obstacle’s
position, generates the extra waypoint, and avoids the collision.

The following paragraphs are part of my dissertation thesis explaining the design decissions.

Obstacle Avoidance
Due to our design decisions, the UAVs are able to fly in different altitudes and search different areas from the other members, achieving collision avoidance between them. However, our last ambition was to give the UAVs the ability to avoid obstacles whose location is known a priori.

Approach
As the 20-sim model representing the physical components of a UAV does not support any kind of sensors for detecting obstacles, our first challenge was to give the UAVs the ability to detect possible obstacles in its determined path. In our approach, the UAV is able to detect an obstacle that its location is known and avoid it, generating a new waypoint. Every time the UAV flies to a new waypoint, it checks whether there is an obstacle in the path between its location and the waypoint’s location. When the UAV reaches a waypoint, it calculates the coordinates of intermediate points from its location to the next waypoint’s location. Figure 5 illustrates our approach. Afterwards, the UAV checks whether the distance between the obstacle’s position and any of these points’ position is less than or equal to a specified radius. If the distance of at least one intermediate point is less than the specified radius, the UAV generates an extra intermediate waypoint so as to avoid the obstacle. If the obstacle’s height is lower than the UAV trajectory’s altitude, then the UAV will generate an intermediate waypoint, increasing its altitude to fly over the obstacle ensuring that it will overpass the obstacle without collision. The new waypoint will have the same position as the intermediate point’s position that its distance is less than the specified radius from the obstacle, and the z- coordinate will be the UAV trajectory’s altitude plus a certain number so as to ensure that the UAV will overpass the obstacle without collision. If the obstacle’s height is too much and hence not efficient for the UAV to fly over it, the UAV will generate an extra waypoint to avoid it. There are three possible scenarios. The first scenario is when the UAV’s trajectory is horizontal or almost horizontal. The second scenario is when the UAV’s trajectory is vertical or almost vertical. The third scenario is when the trajectory that the UAV has to follow does not belong in the aforementioned categories. For every scenario, the UAV generates an avoiding waypoint, minimizing the distance travelled to avoid the obstacle as it can be seen in the following Figures. 

For the intermediate points generation, the equation of a line was used. Since we know two points of the line, the UAV’s current position and the next waypoint’s position, we can calculate the slope of the line. The equation of a line is typically written as . Where  are the coordinates of the first point, and  the coordinates of the second point. Our approach is able to generate intermediate points for all the types of lines vertical, horizontal, and slope intercept line.


