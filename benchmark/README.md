# ROS 1 evaluation protocol

1. Select a sequence from the [challenge spreadsheet](../dataset/Konya_Dataset_Challenge_Quantification.xlsx). Download its bag and available references from the [original dataset](https://github.com/Konya-Dataset/Konya-Dateset#downloads).
2. Inspect the recording with `rosbag info <file.bag>`. Verify required topics, timestamps, calibration and transforms. Record the ROS distribution, algorithm revision, input topics, sensor mode, hardware and configuration ID.
3. Set `/use_sim_time` to `true` before launching the algorithm and replay with `rosbag play --clock <file.bag>`. Reset algorithm state for each run. Record the playback rate, run ID and initialization issues.
4. Export trajectories, maps and logs. Document the reference source and type. Treat SLAM-derived maps as comparison baselines. Use ATE and RPE when a comparable timestamped reference trajectory is available. Document pose alignment, timestamp matching and RPE interval. With a map-only reference, report map agreement and tracking statistics.
5. Record every run, including partial runs and failures, in `02_Test_Results` in the [benchmark workbook](Konya_Dataset_SLAM_Test_Analysis_Template.xlsx). Report completion, tracking loss and false loop closures alongside accuracy. Leave unavailable metrics blank and report the reason in the notes.
6. Compare runs by algorithm, sensor mode and challenge. Preserve missing and comparative labels when interpreting CD, CLS and MCS. Several challenges can occur in the same sequence.

Candidate baselines are Cartographer 2D, Hector SLAM, ORB-SLAM3 and RTAB-Map. Report sensor inputs for each run, since differences in performance may also reflect differences in sensor modality.
