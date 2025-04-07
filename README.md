# Week 2 Day 2: 30 Day DevOps Challenge

## Project: NCAA Highlights Processor

This project is an automated pipeline that fetches, processes, and converts NCAA basketball game highlights using AWS services. It demonstrates a practical implementation of video processing automation using Python and AWS MediaConvert.

## Project Overview

The pipeline consists of four main Python scripts:

1. `fetch.py`: Fetches basketball highlights from RapidAPI's sport highlights service
2. `process_one_video.py`: Downloads the first video from fetched highlights and stores it in S3
3. `mediaconvert_process.py`: Processes the video using AWS MediaConvert for optimization
4. `run_all.py`: Orchestrates the execution of all scripts with retry logic

## Features

### Highlight Fetching (`fetch.py`)

- Retrieves basketball highlights from RapidAPI
- Configurable parameters for date, league, and result limits
- Automatic S3 bucket creation and management
- JSON data storage in S3

### Video Processing (`process_one_video.py`)

- Extracts video URLs from stored JSON data
- Downloads videos using streaming to manage memory efficiently
- Uploads raw videos to S3 for further processing
- Handles various video formats and sizes

### MediaConvert Integration (`mediaconvert_process.py`)

- Configures AWS MediaConvert jobs for video optimization
- Supports H.264 encoding with customizable settings
- Implements high-quality audio processing (AAC)
- Manages output formats and quality settings

### Pipeline Orchestration (`run_all.py`)

- Automated execution of all processing steps
- Robust retry logic for failed operations
- Configurable delays between steps
- Comprehensive error handling and logging

## Pipeline Flow

1. Fetch highlights from RapidAPI
2. Store highlight metadata in S3
3. Download first video from highlights
4. Upload raw video to S3
5. Process video with MediaConvert
6. Store processed video in S3

## AWS Services Used

- Amazon S3: For storing raw and processed videos
- AWS MediaConvert: For video transcoding and optimization
- AWS IAM: For role-based access control
- AWS SDK (boto3): For AWS service interaction
