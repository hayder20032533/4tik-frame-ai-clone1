# 4tik-frame-ai-clone1
Python desktop app for video enhancement with FFmpeg"
# 4Tik Frame AI Clone - Python Video Enhancer

A Python-based desktop application for enhancing videos with various filters and effects, similar to the 4Tik Frame AI tool.

## Features

- **Video Enhancement Options:**
  - Ultra Smooth (Motion Interpolation)
  - Sharpening Filter
  - 2× Upscaling
  - Frame Rate Adjustment (30fps, 60fps, 120fps)
  - LUT Color Grading Support

- **Audio Processing:**
  - 8D Audio Simulation with reverb and stereo widening

- **Quality Settings:**
  - High, Medium, Low quality presets
  - Optimized encoding parameters

- **User-Friendly Interface:**
  - Modern TikTok-inspired design
  - Real-time progress tracking
  - Easy file selection and export

## Installation

### Prerequisites

1. **Python 3.7 or higher**
   - Download from [python.org](https://www.python.org/downloads/)

2. **FFmpeg** (Required for video processing)
   
   **Windows:**
   - Download from [https://ffmpeg.org/download.html](https://ffmpeg.org/download.html)
   - Extract to a folder (e.g., `C:\ffmpeg`)
   - Add `C:\ffmpeg\bin` to your system PATH
   
   **macOS:**
   ```bash
   brew install ffmpeg
   ```
   
   **Linux (Ubuntu/Debian):**
   ```bash
   sudo apt update
   sudo apt install ffmpeg
   ```

3. **Install Python Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. **Run the Application:**
   ```bash
   python app.py
   ```

2. **Using the App:**
   - Click "Choose Video" to select your input video file
   - (Optional) Click "Choose LUT" to apply color grading
   - Enable desired enhancement options:
     - Ultra Smooth: Adds motion interpolation for smoother playback
     - Sharpen: Enhances video sharpness
     - 2× Upscale: Doubles the resolution
     - Frame Rate: Set output frame rate
     - 8D Audio: Applies spatial audio effects
   - Select quality level (High/Medium/Low)
   - Click "Choose Export Folder" to set output location
   - Click "🚀 Export Video" to start processing

## Supported Formats

**Input:** MP4, MOV, AVI, MKV
**Output:** MP4 (H.264 + AAC)
**LUT Files:** .cube, .3dl

## Technical Details

- **GUI Framework:** PyQt5
- **Video Processing:** FFmpeg
- **Threading:** Separate thread for video processing to prevent UI freezing
- **Progress Tracking:** Real-time progress updates during processing

## FFmpeg Filters Used

- **Sharpening:** `unsharp=5:5:1.0:5:5:0.0`
- **Motion Interpolation:** `minterpolate=fps=60:mi_mode=mci:mc_mode=aobmc:vsbmc=1`
- **Upscaling:** `scale=iw*2:ih*2:flags=lanczos`
- **LUT Application:** `lut3d='path/to/lut.cube'`
- **8D Audio:** Combined echo, stereo widening, and compression

## Troubleshooting

### FFmpeg Not Found
If you get "FFmpeg not found" error:
1. Make sure FFmpeg is installed
2. Verify it's in your system PATH by running `ffmpeg -version` in terminal
3. Restart the application after installing FFmpeg

### Processing Errors
- Check that input video file is not corrupted
- Ensure sufficient disk space for output
- Try with lower quality settings if processing fails

### Performance Tips
- Use "Low" quality for faster processing
- Disable unnecessary filters to speed up processing
- Close other applications during processing for better performance

## License

This project is for educational purposes. Make sure to respect copyright laws when processing videos.

## Contributing

Feel free to submit issues, feature requests, or pull requests to improve the application.
from setuptools import setup, find_packages

with open("README.md", "r", encoding="utf-8") as fh:
    long_description = fh.read()

setup(
    name="4tik-frame-ai-clone",
    version="1.0.0",
    author="Your Name",
    author_email="your.email@example.com",
    description="Python desktop app for video enhancement with FFmpeg",
    long_description=long_description,
    long_description_content_type="text/markdown",
    url="https://github.com/yourusername/4tik-frame-ai-clone",
    packages=find_packages(),
    classifiers=[
        "Development Status :: 4 - Beta",
        "Intended Audience :: End Users/Desktop",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
        "Programming Language :: Python :: 3",
        "Programming Language :: Python :: 3.7",
        "Programming Language :: Python :: 3.8",
        "Programming Language :: Python :: 3.9",
        "Programming Language :: Python :: 3.10",
        "Topic :: Multimedia :: Video",
        "Topic :: Multimedia :: Video :: Conversion",
    ],
    python_requires=">=3.7",
    install_requires=[
        "PyQt5>=5.15.0",
    ],
    entry_points={
        "console_scripts": [
            "4tik-enhancer=app:main",
        ],
    },
    include_package_data=True,
    package_data={
        "": ["sample_luts/*.cube", "*.md"],
    },
)
