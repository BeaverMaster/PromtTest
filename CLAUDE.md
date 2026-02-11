# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains a **prompt specification** (`Promt/Promt`) for generating an iOS Home-Screen Weather Web App (PWA-style). The prompt is written in German and defines strict rules for code generation.

## Key Specifications from the Prompt

- **Single-file architecture**: One HTML file containing all markup, styles, and JS
- **Tech stack**: HTML + Tailwind CSS (CDN) + Vanilla JavaScript — no frameworks, no TypeScript, no multi-file structure
- **API**: Open-Meteo Forecast API exclusively (no alternatives, no caching)
- **State management**: Central `const state = {}` object with mandatory functions: `loadState()`, `saveState()`, `fetchWeather()`, `detectLocation()`, `setCityManually()`, `render()`, `bindEvents()`, `init()`
- **Rendering rule**: All UI generated inside `render()` via template strings, replacing `#app` innerHTML. No direct DOM mutation outside `render()`. No inline event handlers.
- **Dark/Light mode**: Automatic based on sunrise/sunset times from the API, not user preference

## Workflow

There is no build step, linter, or test suite. The output is a single static HTML file opened directly in a browser.

## Language

The prompt and project context are in **German**. Respond in German when working with this project unless asked otherwise.
