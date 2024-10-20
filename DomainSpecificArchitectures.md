# Warehouse-Scale Video Acceleration: Co-Design and Deployment in the Wild

## Paper

Warehouse-Scale Video Acceleration: Co-Design and Deployment in the Wild \
Parthasarathy Ranganathan, Daniel Stodolsky, Jeff Calow, Jeremy Dorfman, Marisabel Guevara, Clinton Wills Smullen IV, Aki Kuusela, et al. \
Proceedings of the International Conference on Architectural Support for Programming Languages and Operating Systems (ASPLOS), April 2021.

## Problem Description and Motivation

This paper looks at how to improve video processing efficiency in data centers, especially with the massive rise in video-related workloads like YouTube, video conferencing, and cloud gaming. These workloads are becoming harder to manage due to the slowing of Moore’s Law, which limits improvements in general-purpose processors. Since video is a big part of internet traffic today, especially with higher resolutions and new formats, there’s a need for specialized hardware to handle video transcoding efficiently at warehouse scale. The authors aim to solve this problem by creating a specialized video processing system that can handle video encoding more effectively than traditional CPU-based systems.

## Main Ideas/Approach

The authors propose a video acceleration system built around a new hardware component called the Video Coding Unit (VCU), which is specifically designed for video transcoding at large scale. Their approach includes several key components:

1. **Video Coding Unit (VCU)**: This is the core hardware accelerator used for encoding and decoding video, optimized for formats like H.264 and VP9. The VCU reduces the heavy computational load from the CPU and improves performance.
2. **Hardware-Software Co-design**: The system integrates the VCU with data center infrastructure. It’s not just about hardware; the software is also co-designed to work efficiently with these accelerators, optimizing resource use and improving scheduling.
3. **Multiple-Output Transcoding (MOT)**: The VCU allows multiple versions of a video to be processed simultaneously. For example, a video can be transcoded into different resolutions and formats without needing to decode it multiple times.
4. **High-Level Synthesis (HLS)**: The design of the VCU uses HLS, which allows the system to be flexible and adaptable, letting engineers make changes or add features late in the development process.

## Strengths and Weaknesses

### Strengths
- **High Performance**: The VCU-based system shows a huge performance improvement (20-33x) compared to traditional CPU systems, especially in handling large-scale video workloads.
- **Scalability**: The system is designed to scale across data centers, making it highly suitable for large companies like Google that handle massive amounts of video content.
- **Flexibility**: The use of HLS and tight integration with software gives the system flexibility, allowing for easier updates and optimizations even after deployment.

### Weaknesses
- **Complexity**: Introducing specialized hardware like the VCU adds complexity to the system, especially when it comes to fault tolerance and handling failures in a large-scale environment.
- **Resource Demand**: While it offers great performance, the VCU requires a lot of memory bandwidth and power, which might raise concerns about cost-effectiveness in some scenarios.

## Questions for Discussion
- Something interesting I saw was the power law watch time - 80% of watch time on 20% of videos. How does this affect resource distribution in a system like this? Do you even need to make VCU hardware available for all videos, or just the ones you presume will be most popular?