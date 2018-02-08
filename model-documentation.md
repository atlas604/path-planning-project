#  Reflection on Path Generation

Based on the Q&A video, this model expands that approach utilizing finite state machines to transition or maintain in the same lane.  

We use many logical operations to determine these state transitions and since there aren’t many different states, this solution is quite effective.  The car will prioritize changing lanes only if there’s sufficient space in one of the adjacent lanes; otherwise it will slowly decrease in velocity until sufficient space is available.

Using the available waypoints provided we can convert these in frenet coordinates generate a path unaffected by the curvature of the road.  Furthermore, we sufficiently space each waypoint to help each transition become smoother and less prone to sudden change in position and velocity which ultimately minimizes jerk.  

To help waypoint transition, the model utilizes spine to help interpolate the car’s position relative to the waypoints.  With this, we can estimate the desired position between the waypoints for more optimal path planning while remaining in the lane.  This is implemented in the header file (src/spline.h).   


# Improvement

Of course, implementing a cost function can make the decisions more optimal on whether or not to maintain a certain speed or remain in the lane as opposed to prioritize changing lanes which is what the current model operates on.

In addition, opposing traffic and surrounding cars can behave erratically and cause unforeseeable accidents. Having more state transitions or a prediction module of their movement based on their velocity and yaw could help improve the safety of our car.      
