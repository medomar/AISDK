# AISDK - Claude Code Context

## Documentation Sync Rule

**When making changes to the SDK, update this file to reflect:**
- New providers added
- API changes
- New models or protocols
- Breaking changes

---

## Overview

This is a **public Swift Package** providing a unified interface for AI communication. It supports multiple providers (Claude, OpenAI, Ollama) with a consistent API.

## Parent Project

For full project context, see the root `CLAUDE.md` at `../CLAUDE.md`

## Purpose

The SDK abstracts AI provider differences so the main app can:
- Switch between providers easily
- Support both cloud and local AI
- Handle streaming responses uniformly
- Manage tokens/credits consistently

## Tech Stack

| Component | Technology |
|-----------|------------|
| Package Type | Swift Package (SPM) |
| Min iOS | 16.0 |
| Min macOS | 13.0 |
| Concurrency | async/await, AsyncSequence |
| Networking | URLSession |

## Supported Providers

| Provider | Type | Models |
|----------|------|--------|
| Claude (Anthropic) | Cloud | claude-3-opus, claude-3-sonnet, claude-3-haiku |
| OpenAI | Cloud | gpt-4o, gpt-4-turbo, gpt-3.5-turbo |
| Ollama | Local | llama3, mistral, codellama, etc. |

## Package Structure

```
AISDK/
├── Package.swift
├── Sources/
│   └── AISDK/
│       ├── AISDK.swift              # Public API
│       ├── Models/
│       │   ├── AIMessage.swift
│       │   ├── AIResponse.swift
│       │   ├── AIModel.swift
│       │   └── AIError.swift
│       ├── Providers/
│       │   ├── AIProvider.swift     # Protocol
│       │   ├── ClaudeProvider.swift
│       │   ├── OpenAIProvider.swift
│       │   └── OllamaProvider.swift
│       └── Utilities/
│           ├── TokenCounter.swift
│           └── StreamParser.swift
└── Tests/
    └── AISDKTests/
```

## Public API

```swift
// Initialize with provider
let ai = AISDK(provider: .claude(apiKey: "..."))

// Simple completion
let response = try await ai.complete(prompt: "Hello")

// Streaming completion
for try await chunk in ai.stream(prompt: "Hello") {
    print(chunk.text)
}

// Chat with history
let messages: [AIMessage] = [
    .system("You are a helpful assistant"),
    .user("Hello")
]
let response = try await ai.chat(messages: messages)

// Switch provider
ai.setProvider(.ollama(baseURL: "http://localhost:11434"))
```

## Provider Protocol

```swift
protocol AIProvider {
    func complete(prompt: String, model: AIModel?) async throws -> AIResponse
    func stream(prompt: String, model: AIModel?) -> AsyncThrowingStream<AIChunk, Error>
    func chat(messages: [AIMessage], model: AIModel?) async throws -> AIResponse
    func models() async throws -> [AIModel]
}
```

## Integration with Main App

The main `SocialMediaApp` imports this SDK:

```swift
// Package.swift dependency
.package(path: "../AISDK")

// Import in Swift files
import AISDK
```

## Common Commands

```bash
# Build package
swift build

# Run tests
swift test

# Generate Xcode project (optional)
swift package generate-xcodeproj
```

## Key Files for AI Integration

| File | Purpose |
|------|---------|
| `AIProvider.swift` | Provider protocol definition |
| `ClaudeProvider.swift` | Anthropic Claude API integration |
| `OpenAIProvider.swift` | OpenAI API integration |
| `OllamaProvider.swift` | Local Ollama integration |
| `TokenCounter.swift` | Token estimation for cost tracking |
