# 🤖 MuAPI for Claude Code — Official Claude Code Plugin for muapi.ai

> **Generate images, videos, audio, and more with 100+ AI models directly inside Claude Code.** A one-command MCP plugin that brings the full muapi.ai generative media platform into your IDE — no browser switching, no copy-pasting URLs.

[![Install in Claude Code](https://img.shields.io/badge/Claude%20Code-Install%20Plugin-blue)](https://muapi.ai)
[![muapi.ai](https://img.shields.io/badge/muapi.ai-platform-orange)](https://muapi.ai)
[![MCP](https://img.shields.io/badge/MCP-stdio-green)](https://modelcontextprotocol.io)
[![npm](https://img.shields.io/npm/v/muapi-claude-code)](https://www.npmjs.com/package/muapi-claude-code)

---

## ⚡ Install

```bash
claude mcp add muapi -- npx -y muapi-claude-code
```

Then set your API key (get one free at [muapi.ai/access-keys](https://muapi.ai/access-keys)):

```bash
claude mcp add muapi --env MUAPI_KEY=your_key_here -- npx -y muapi-claude-code
```

That's it. Restart Claude Code and the tools are live.

---

## 🛠️ What You Can Do

Once installed, just ask Claude naturally:

| What to say | What happens |
|---|---|
| `"Generate a product photo of a red sneaker on white background"` | Calls `generate_image` with flux-dev |
| `"Make a 5-second cinematic video of ocean waves at sunset"` | Calls `generate_video` with kling-master |
| `"Animate this image into a video"` *(attach URL)* | Calls `video_from_image` |
| `"Remove the background from this product photo"` | Calls `enhance_bg_remove` |
| `"Upscale this image to 4x resolution"` | Calls `enhance_upscale` |
| `"Create a lo-fi hip hop track, 30 seconds, instrumental"` | Calls `audio_create` with Suno |
| `"Apply Ghibli style to this photo"` | Calls `enhance_ghibli` |
| `"Swap the face in this image"` | Calls `enhance_face_swap` |
| `"What's my muapi credit balance?"` | Calls `account_balance` |

---

## 🧰 Available Tools

### Image Generation
| Tool | Models |
|------|--------|
| `generate_image` | flux-dev, flux-schnell, flux-kontext-dev/pro/max, hidream-fast/dev/full, gpt4o, midjourney, seedream, reve, qwen, wan2.1 |
| `edit_image` | flux-kontext-dev/pro/max/effects, gpt4o, reve, seededit, midjourney-i2i/style/omni, qwen |

### Video Generation
| Tool | Models |
|------|--------|
| `generate_video` | veo3, veo3-fast, kling-master, wan2.1/2.2, seedance-pro/lite, hunyuan, runway, pixverse, minimax-std/pro |
| `video_from_image` | veo3, veo3-fast, kling-std/pro/master, wan2.1/2.2, seedance, hunyuan, runway, pixverse, midjourney, minimax |

### Image Enhancement
| Tool | Description |
|------|-------------|
| `enhance_upscale` | AI super-resolution — 2x / 4x |
| `enhance_bg_remove` | Remove or swap backgrounds |
| `enhance_face_swap` | Face swap in images or videos |
| `enhance_ghibli` | Studio Ghibli style transfer |
| `enhance_anime` | Anime style transfer |
| `enhance_colorize` | Colorize black & white photos |
| `enhance_product_shot` | AI product photography |
| `enhance_object_erase` | Erase objects from images |
| `enhance_extend` | Outpaint / extend image borders |

### Video Editing
| Tool | Description |
|------|-------------|
| `edit_lipsync` | Sync lip movements to audio (sync, latentsync, creatify, veed) |
| `edit_effects` | Apply cinematic effects to videos |
| `edit_dance` | Add dance motion to a person |
| `edit_dress` | Change outfit on a person |

### Audio
| Tool | Description |
|------|-------------|
| `audio_create` | Generate original music with Suno |
| `audio_from_text` | Generate sound effects with MMAudio |

### Utilities
| Tool | Description |
|------|-------------|
| `upload_file` | Upload a local file to muapi CDN and get a URL |
| `get_result` | Poll for the result of any async job by request_id |
| `account_balance` | Check your current credit balance |
| `list_models` | List all available models by category |

---

## ⚙️ Configuration

### Environment Variables

| Variable | Description |
|----------|-------------|
| `MUAPI_KEY` | Your muapi.ai API key *(required)* |

### Claude Code project config (`.mcp.json`)

```json
{
  "mcpServers": {
    "muapi": {
      "command": "npx",
      "args": ["-y", "muapi-claude-code"],
      "env": {
        "MUAPI_KEY": "your_key_here"
      }
    }
  }
}
```

### Global config (`~/.claude/mcp.json`)

```json
{
  "mcpServers": {
    "muapi": {
      "command": "npx",
      "args": ["-y", "muapi-claude-code"],
      "env": {
        "MUAPI_KEY": "your_key_here"
      }
    }
  }
}
```

---

## 🔄 How Async Generation Works

Most generation jobs return a `request_id` immediately. The plugin automatically polls until the job completes and returns the output URL(s) — no manual polling needed.

```
ask Claude → tool call → POST /api/v1/{model} → { request_id: "abc123" }
                                                          ↓ auto-polls every 3s
                                              { status: "completed", outputs: ["https://cdn.muapi.ai/..."] }
```

---

## 🔗 Related

| Resource | Link |
|----------|------|
| muapi.ai platform | [muapi.ai](https://muapi.ai) |
| Get API key | [muapi.ai/access-keys](https://muapi.ai/access-keys) |
| REST API docs | [api.muapi.ai/docs](https://api.muapi.ai/docs) |
| muapi CLI | [github.com/SamurAIGPT/muapi-cli](https://github.com/SamurAIGPT/muapi-cli) |
| MCP server (all clients) | [github.com/SamurAIGPT/muapi-mcp-server](https://github.com/SamurAIGPT/muapi-mcp-server) |
| n8n nodes | [github.com/SamurAIGPT/n8n-nodes-muapi](https://github.com/SamurAIGPT/n8n-nodes-muapi) |
| ComfyUI nodes | [github.com/SamurAIGPT/muapi-comfyui](https://github.com/SamurAIGPT/muapi-comfyui) |

---

## 📄 License

MIT Licensed.
