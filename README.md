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
```

## Notes

Generated images should be treated as candidate synthetic data, not automatically trusted training data.

This is intentionally framed as an open scenario, not a tightly specified implementation task. Contributors are expected to apply their own thinking to:

- model/provider selection
- prompt design
- variation configuration
- metadata schema
- quality review approach
- cost estimation
- reporting format

Strong submissions will balance realism, traceability, repeatability, and honest limitation reporting.

## Submission Guidelines

- Fork the repository and create a feature branch for your contribution.
- Submit your work through a pull request against the main repository. Do not submit code, generated images, or datasets through email, chat, or shared drives.
- Open an issue first if your proposed approach changes the scope materially, introduces a major dependency, uses a paid provider by default, or requires a different runtime than the one described in this README.
- Include a short solution approach in the pull request that explains the model/provider choice, prompting strategy, generation workflow, design tradeoffs, and known limitations.
- Include architecture documentation that shows the main components, data flow, provider adapter boundaries, configuration files, and output artifacts. A simple diagram is preferred where useful.
- Include setup and running instructions that allow a reviewer to run the project from a clean checkout.
- Include deployment notes, even if the project only runs locally. State the expected runtime, environment variables, provider configuration, credential handling, storage paths, and optional services.
- Include scaling notes that explain what would need to change for larger image sets, batch generation, retries, rate limits, cloud storage, queues, or managed compute.
- Include integration notes describing how the implementation could later plug into a broader synthetic data generation or dataset preparation workflow without depending on hidden internal APIs.
- Include code documentation for public functions, configuration options, CLI commands, prompt templates, provider adapters, data formats, and output folders.
- Include sample inputs and outputs using only open, synthetic, or contributor-created data. Do not include private, proprietary, customer, or restricted-license data.
- Include tests or validation checks for core behavior, such as manifest creation, metadata completeness, cost/latency logging, provider error handling, and export format.
- Include a short quality report or evidence section showing generated examples, run metadata, known failure cases, and how reviewers should inspect the outputs.
- Pricing and token/cost values should be configurable. Do not hardcode provider pricing as permanent truth.
- Keep secrets, credentials, API keys, generated caches, large output folders, and local environment files out of the repository.
- Add or update `.gitignore` where needed to prevent accidental submission of local data, generated artifacts, or credentials.
- Use clear commit messages and keep unrelated refactors out of the pull request.
- The pull request should be reviewable as a standalone contribution: reviewers should not need access to internal roadmaps, private datasets, or proprietary platform details to understand or run it.
