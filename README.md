How Does DepthAI Provide Spatial AI Results?  
--------------------------------------------
There are two ways to use DepthAI to get Spatial AI results: 
    Monocular Neural Inference fused with Stereo Depth.  
        In this mode the neural network is run on a single camera and fused with disparity depth results. The left, right, or RGB camera can be used to run the neural inference.

    Stereo Neural Inference.  
        In this mode the neural network is run in parallel on both the left and right stereo cameras to produce 3D position data directly with the neural network.

In both of these cases, standard neural networks can be used. There is no need for the neural networks to be trained with 3D data.

DepthAI automatically provides the 3D results in both cases using standard 2D-trained networks, as detailed here [https://docs.luxonis.com/en/latest/pages/faq/#nodepthrequired]. These modes have differing minimum depth-perception limits, detailed here [https://docs.luxonis.com/en/latest/pages/faq/#nodepthrequired].


Monocular Neural Inference fused with Stereo Depth 
In this mode, DepthAI runs object detection on a single cameras (user’s choice: left, right, or RGB) and the results are fused with the stereo disparity depth results. The stereo disparity results are produced in parallel and in real-time on DepthAI (based on semi global matching (SGBM)).

DepthAI automatically fuses the disparity depth results with the object detector results and uses this depth data for each object in conjunction with the known intrinsics of the calibrated cameras to reproject the 3D position of the detected object in physical space (X, Y, Z coordinates in meters).

And all of these calculations are done onboard to DepthAI without any processing load to any other systems. This technique is great for object detectors as it provides the physical location of the centroid of the object - and takes advantage of the fact that most objects are usually many pixels so the disparity depth results can be averaged to produce a more accurate location.


