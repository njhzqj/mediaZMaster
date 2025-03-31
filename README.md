# mediaZMaster

A powerful Python media processing library designed for AI applications.

## Features

- Simple and intuitive API with chainable operations
- Comprehensive video, audio, and image processing capabilities
- Asynchronous processing support
- High-performance implementation based on FFmpeg and OpenCV
- Extensible plugin system

## Installation

```bash
pip install mediaZMaster
```

## Quick Start

### Video Processing

```python
from mediaZMaster import Video

# Simple chainable API
video = Video('input.mp4')
result = (video
          .trim(start=10, end=60)
          .resize(width=720)
          .add_text("Hello World")
          .save('output.mp4'))
```

### Audio Processing

```python
from mediaZMaster import Audio

audio = Audio('input.mp3')
audio.extract_from(video_file='video.mp4')
audio.apply_fade(in_duration=2, out_duration=3)
audio.save('output.mp3')
```

### Image Processing

```python
from mediaZMaster import Image

image = Image('input.jpg')
image.resize(width=800).apply_filter('grayscale').save('output.jpg')
```

### Asynchronous Processing

```python
import asyncio
from mediaZMaster import Video

async def process_video():
    video = Video('large_file.mp4')
    task = video.resize(1080).to_async()
    
    # Do other things while processing
    while not task.done():
        print(f"Progress: {task.progress}%")
        await asyncio.sleep(1)
    
    result = await task.result()
    return result

asyncio.run(process_video())
```

## Documentation

For detailed documentation, visit [docs/](docs/)

## License

MIT
