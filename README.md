# Turtlebot3_Multi_Map_Merge

 * Multi-Map Merge node in the actual turtlebot3_simulations package doesn't work as expected.
 * Reason for the same was because the multi_turtlebot3.launch file didn't publish odomotery for each turtlebot3 bot spawned
     * This was confirmed by looking at the tf_tree of the launched simulation.
 * In multi_turtlebot3.launch file , the tf_prefix tag in placed wrongly inside node robot_state_publisher
 * Adding the tf_prefix inside each group tag of turtlebot fixes the odometry problem
    * Now odomtery is published for each bot under it's namespace by gazebo
 * Now upon launching the slam node for turtlebot3 , it's defined for only bot at a time.
 * So I created a new launch file :
    * It launches the updated multi_turtlebot3.launch file
    * Then it launches the slam node three times for each turtlebot in the simulation  
    
    > Now map made by each bot is published by slam node for each bot in the tf_tree 
 * Finally launch the multi_map_merge.launch file to combine the maps of individual bots into one single map node.
