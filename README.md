# Generative Tree Image Variation

## Overview

Build a reusable generative image variation scenario using open or synthetic tree images, prompt-driven variation requests, model-provider adapters, and benchmark-ready output tracking.

This scenario should focus on using image-generation or image-editing models to create semantic tree variations that are difficult to achieve with classical augmentation alone, such as age, season, health condition, leaf density, lighting, and environmental context.

The contribution should remain self-contained, use only open or synthetic images, and avoid dependency on any internal platform, private dataset, or proprietary model workflow.

## Problem Statement

Given a limited number of base tree images and a set of requested variation parameters, generate realistic tree image variants using an image-generation or image-editing model.

The solution should demonstrate a practical workflow that can:

- take base images and variation prompts as input
- generate new tree image variants
- record model, prompt, cost, token, and latency metadata
- preserve source image traceability
- support review of generated image quality
- produce outputs that can later be benchmarked against classical augmentation results

## Scope

The scenario should focus on:

- open or synthetic base tree images
- image-to-image or prompt-based image generation
- semantic variations such as:
  - young tree vs mature tree
  - healthy vs stressed tree
  - seasonal appearance
  - leaf density
  - lighting
  - weather
  - background setting
  - camera perspective where supported
- provider/model abstraction where practical
- prompt templates
- output metadata manifest
- cost, token, and latency tracking
- simple visual review gallery or report

## Non-Goals

This work item is not intended to cover:

- internal model training
- proprietary image datasets
- proprietary species or disease taxonomy
- production botanical validation
- production MLOps
- enterprise provider routing
- tenant-level security or access control
- claims that generated images are automatically valid training data

## Suggested Stack

To stay broadly aligned with practical open contribution workflows, contributions should preferably use:

- Python
- provider SDKs or HTTP APIs where appropriate
- Pillow or OpenCV for image handling
- JSON or JSONL for run logs
- YAML or JSON for generation config
- simple static HTML gallery or notebook for review

Model choices may include publicly accessible image-generation or image-editing APIs. For example, Google describes Nano Banana as Gemini's native image-generation capability, including `gemini-2.5-flash-image`. Pricing should be configurable because provider prices change.

## Data Expectations

The base image set should use only:

- openly licensed images
- contributor-created images
- synthetic placeholder images

The generated output manifest should preferably capture:

- run ID
- source image ID
- generated image ID
- requested variation
- prompt template ID
- final prompt used
- provider
- model name
- model version, if available
- input token count, if available
- output token count or image count
- configured unit price
- estimated cost
- latency
- output file path
- generation timestamp
- validation or reviewer status

## Expected Deliverables

A good submission should include:

- a working generative image variation pipeline
- at least one provider/model adapter
- sample prompt templates
- generated sample outputs
- output metadata manifest
- cost and latency report
- simple visual review gallery or notebook
- documentation covering setup, usage, assumptions, limitations, and provider configuration

## Success Criteria

A submission will be considered successful if:

- it is runnable and understandable by reviewers
- it uses open or synthetic data only
- it generates semantic tree variations from base images or prompts
- every generated image is traceable to its source image or prompt
- prompt, model, cost, token, and latency metadata are captured where available
- outputs can be visually reviewed
- the scenario can later be compared against a classical augmentation scenario on cost, speed, quality, and variation usefulness

## Shared Benchmark Fields

To support later comparison with other image-generation approaches, the scenario should preferably emit a manifest such as `generation_manifest.jsonl` or `generation_manifest.csv`.

Minimum useful fields:

```json
{
  "run_id": "string",
  "method": "generative_model",
  "source_image_id": "string",
  "generated_image_id": "string",
  "requested_variation": {},
  "provider": "string",
  "model": "string",
  "prompt": "string",
  "input_tokens": 0,
  "output_tokens": 0,
  "output_image_count": 1,
  "unit_price_config": {},
  "estimated_cost_usd": 0,
  "latency_ms": 0,
  "output_file": "string",
  "metadata_complete": true,
  "review_status": "pending"
}
