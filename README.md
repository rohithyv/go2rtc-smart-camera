# Smart Camera Streaming Platform

A Go-based real-time camera streaming platform for working with IP camera streams across RTSP, WebRTC, HLS, and other media protocols.

This repository is based on the open-source **go2rtc** project and is maintained here as a portfolio project focused on understanding real-time video streaming, camera integrations, media processing, and backend service architecture.

## Tech Stack

- Go
- RTSP
- WebRTC
- HLS
- FFmpeg
- HTTP / WebSocket APIs
- Docker
- YAML configuration

## Core Features

- Real-time IP camera streaming
- RTSP camera ingestion
- WebRTC low-latency browser streaming
- HLS video streaming
- HTTP and WebSocket APIs
- FFmpeg-based transcoding and media processing
- Multi-source stream handling
- Camera stream monitoring and statistics
- Docker-based deployment

## Architecture

```text
IP Camera
    |
    | RTSP
    v
+-------------------+
| Streaming Service |
|       Go          |
+-------------------+
        |
        +------------------+
        |                  |
        v                  v
     WebRTC              HLS
        |                  |
        +--------+---------+
                 |
                 v
            Web Browser

        FFmpeg
          |
          v
 Transcoding / Processing
```

## Supported Streaming Protocols

### Input

- RTSP
- WebRTC
- HLS
- RTMP
- MJPEG
- ONVIF

### Output

- WebRTC
- HLS
- RTSP
- MP4
- MJPEG
- RTMP

## Local Setup

Clone the repository:

```bash
git clone https://github.com/rohithyv/go2rtc-smart-camera.git
cd go2rtc-smart-camera
```

Run the application:

```bash
go run .
```

The web interface is available at:

```text
http://localhost:1984
```

## Camera Configuration

Create or update `go2rtc.yaml`:

```yaml
streams:
  camera1:
    - rtsp://username:password@camera-ip/stream
```

The service uses:

```text
HTTP API / Web UI : 1984
RTSP              : 8554
WebRTC            : 8555
```

## Example Streaming Flow

```text
RTSP Camera
    |
    v
Streaming Server
    |
    +--------> WebRTC --------> Browser
    |
    +--------> HLS -----------> Web Player
    |
    +--------> RTSP ----------> External Client
```

## FFmpeg Processing

FFmpeg can be used when a camera codec is not directly compatible with the target client.

Example workflow:

```text
Camera Stream
     |
     v
   FFmpeg
     |
 Transcoding
     |
     v
WebRTC / HLS / RTSP
```

This enables codec conversion and media processing without requiring transcoding for every stream.

## API

The platform includes HTTP and WebSocket APIs for interacting with active camera streams and retrieving streaming information.

Example:

```text
GET /api/streams
```

The API can be used to inspect active streams, connection information, codecs, and streaming status.

## Docker

The application can also run as a containerized service.

Example:

```bash
docker run --rm \
  -p 1984:1984 \
  -p 8554:8554 \
  -p 8555:8555/tcp \
  -p 8555:8555/udp \
  alexxit/go2rtc
```

## Security

Camera credentials should never be committed directly to the repository.

Use environment-specific configuration and avoid exposing RTSP, HTTP API, or WebRTC ports publicly without appropriate network controls and authentication.

## What I Explored

Through this project, I focused on:

- Understanding concurrent Go-based streaming services
- RTSP camera ingestion and stream routing
- WebRTC low-latency browser video delivery
- HLS streaming
- FFmpeg media transcoding
- HTTP and WebSocket APIs
- Camera codec compatibility
- Docker-based service deployment
- Real-time media system architecture
- Stream health and connection monitoring

## Original Project

This repository is based on the open-source **go2rtc** project created by AlexxIT.

Original project:

https://github.com/AlexxIT/go2rtc

All original licensing and attribution are preserved.
