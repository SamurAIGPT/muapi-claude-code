# MuAPI Claude Code MCP Server

MCP server for integrating MuAPI with Claude Code and other MCP-compatible clients.

## Features

* Account Balance
* Image Generation
* Video Generation
* Image Editing
* Image-to-Video
* File Uploads
* Model Discovery
* Prediction Tracking

## Installation

Clone the repository:

```bash
git clone <repository-url>
cd muapi-claude-code
```

Install dependencies:

```bash
npm install
```

The server uses the published MuAPI JavaScript SDK:

```bash
npm install muapi-js
```

## Configuration

Create a `.env` file:

```env
MUAPI_API_KEY=your_api_key_here
```

## Run

```bash
node src/index.js
```

## Available Tools

* account_balance
* generate_image
* generate_video
* edit_image
* image_to_video
* upload_file
* list_models
* model_details
* get_prediction

## Example

Generate an image:

```text
Generate an image of a futuristic city at sunset
```

Generate a video:

```text
Generate a cinematic drone shot over mountains
```

## SDK

Powered by the published MuAPI JavaScript SDK:

```bash
npm install muapi-js
```
