# README #

This README would normally document whatever steps are necessary to get your application up and running.

### What is this repository for? ###

* This is a cross camera object tracking system for visual surveillance, including the Tracking Manager, Tracking Algorithm module and an Analyzer for showing the result.
* The Tracking Manager responsible for maintaining all resources that will be dispatched to all cameras(e.g. IP camera) in the system, including the object feature data transferring and the data format definition etc. On the other hand, the entry/exit zone mapping function(algorithm) between those cameras will be implemented in this module soon.
* The Tracking Algorithm implemented with an open source framework TLD(tracking-learning-detection) at present, and is build as a library for easy to replace. Now, this algorithm seems not good for object re-identification in multi-object tracking since its feature is not robust(only color histogram). I will try to add some new features or use other algorithm such as ELM for making this better.
* Finally, the Analyzer will invoke the tracking API for doing the object tracking for one camera and showing the result by use of openCV.

### How do I get set up? ###

* To run this system, make sure that you have already installed FFMpeg, openCV (2.4.9 or later).
* First, you should run the Tracking Manager for create the resource for the system.
* ex: TrackingManager -t 2 -m 4, which "-t" means how many cameras will be used and "-m" the max number of targets in each single camera.
* After running Tracking Manager, you can execute the AnalyzerTK for doing the tracking, and the parameters are defined below:
* * "-c" to give the camera ID in integer.
* * "-k" to set up an interval in ms to keep tracking an object which has disappeared from that moment.
* * "-l" is the detection model file path trained by Adaboost(openCV).
* * "-r" describe which tracking algorithm will be loaded (in this system will be "TLD").
* * "-v" set up the IP camera URL.
* If you want to build a cross camera system, please execute the Analyzer once for each camera and input different camera IDs and URLs as parameters described above respectively.