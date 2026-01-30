# AISDK

A Swift SDK for unified AI communication - supporting Claude, OpenAI, and local models (Ollama).

[![Swift 5.9+](https://img.shields.io/badge/Swift-5.9+-orange.svg)](https://swift.org)
[![Platform](https://img.shields.io/badge/Platform-macOS%2013%2B%20%7C%20iOS%2016%2B-blue.svg)]()
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## Overview

AISDK provides a unified interface for interacting with multiple AI providers, making it easy to:

- Switch between cloud and local AI models
- Handle streaming responses
- Manage API credentials securely
- Build AI-powered applications

## Installation

### Swift Package Manager

Add AISDK to your `Package.swift`:

```swift
dependencies: [
    .package(url: "https://github.com/medomar/AISDK", from: "1.0.0")
]
```

Or in Xcode: **File → Add Package Dependencies** → Enter the repository URL.

## Quick Start

```swift
import AISDK

// Initialize a provider
let claude = ClaudeProvider(apiKey: "your-api-key")

// Generate content
let response = try await claude.generate(
    prompt: "Write a social media post about productivity",
    model: .sonnet
)

print(response.text)
```

## Supported Providers

| Provider | Status | Models |
|----------|--------|--------|
| Claude (Anthropic) | Planned | Opus, Sonnet, Haiku |
| OpenAI | Planned | GPT-4o, GPT-4, GPT-3.5 |
| Ollama (Local) | Planned | Llama, Mistral, etc. |

## Features

### Unified Interface

```swift
// Same interface for all providers
protocol AIProvider {
    func generate(prompt: String, model: AIModel) async throws -> AIResponse
    func stream(prompt: String, model: AIModel) -> AsyncThrowingStream<String, Error>
}
```

### Streaming Responses

```swift
for try await chunk in provider.stream(prompt: "Tell me a story") {
    print(chunk, terminator: "")
}
```

### Local AI (Ollama)

```swift
// Use local models - no API costs!
let ollama = OllamaProvider(host: "http://localhost:11434")
let response = try await ollama.generate(
    prompt: "Your prompt",
    model: .llama3
)
```

## Requirements

- Swift 5.9+
- macOS 13+ / iOS 16+
- Xcode 15+

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Security

For security issues, please see [SECURITY.md](SECURITY.md).

## License

AISDK is available under the MIT License. See [LICENSE](LICENSE) for details.

---

Made with care for the Swift community.
