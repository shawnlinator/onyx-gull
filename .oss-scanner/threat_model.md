# Threat model

## What this project does and where untrusted input enters
A media server (C#/.NET). Untrusted input: HTTP requests, media library metadata (tags in
containers), transcoding parameters, and the realtime (WebSocket) API. Parsing of untrusted
media-container metadata and the HTTP layer are the main surfaces.

## Components that matter most / least
- most: the HTTP/REST and WebSocket layers, media-metadata parsing, and the transcoding command
  assembly (external-process arguments).
- less: the web client.

## How to exercise it
Serve crafted media files with hostile metadata; exercise the REST/WebSocket API; test the
transcoding argument construction.

## How you rate severity
- RCE (e.g., command injection in transcoding) or auth bypass: critical.
- Path traversal in library access: high. XSS: medium. DoS: medium.

## Anything to leave alone
- Do not report the web client bundle; focus on the server.
