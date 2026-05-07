# Generative Tree Image Creation Challenge

## Background

[FloCard](https://flocard.app) is a sustainability-focused digital platform that combines digital identity, community engagement, climate action, and nature-based project tools. The platform supports businesses, communities, and sustainability initiatives through features such as digital business cards, sustainability profiles, carbon offsetting, project development, and tools aligned with climate and SDG goals.

FloCard also has a Tree Planters App used by communities, planters, and farms working on afforestation projects.

The app helps users digitally tag and trace trees using:

- geo-tagged single tree images
- Google Map based boundary tagging for clusters of trees or forest areas
- mobile app or mobile browser based field capture
- offline capture support for areas with low or no internet connectivity

Tree tagging usually happens in remote or low-connectivity areas. Users capture the tree image and location first. Later, when internet connectivity is available, the captured assets are synced and edited with details such as species, age, date of plantation, and related information. After review and approval, the tree record becomes a blockchain-based tree asset.

## Current Tree Tagging Flow

The tree asset creation process broadly follows three steps:

1. A user captures a tree image and geo-tag in the mobile app or mobile browser, often in offline mode.
2. The asset is synced later and edited with details such as species, age, plantation date, and other metadata.
3. The asset goes through an approval step before becoming a blockchain-based asset.

This process works, but it depends heavily on the quality of the image and the accuracy of manually entered tree details.

## Problem Statement

During tree tagging, users may accidentally capture non-tree images, unclear tree images, or images where the tree species is difficult to identify.

Even when the image is valid, users may not always know:

- the correct species
- the age of the tree
- the health or visible condition of the tree
- whether the image is good enough for review

These details are important because tree species, age, and health are used to estimate carbon or GHG offset potential. Incorrect metadata can affect downstream reporting and asset quality.

FloCard is exploring an AI-assisted workflow where tree images captured during the tagging process can be analyzed to help identify whether the image contains a tree, estimate the species, and provide tentative age and health indicators.

To build and train such models, a large quantity of training images is needed across different tree species, ages, seasons, health conditions, locations, lighting conditions, and capture qualities. The initial focus is on tree species common in eastern India, with the possibility of expanding later.

## Challenge Objective

Build a solution that can take a limited number of seed images or species prompts and generate a larger set of realistic synthetic tree images using a generative AI image model.

The preferred direction is a locally runnable or self-hostable generative AI workflow, so the solution can be tested without depending entirely on a paid hosted API. 

## Expected Outcome

A useful solution should be able to:

- accept seed images, prompts, or both
- generate many realistic synthetic tree images
- allow customization of generation parameters
- preserve traceability between inputs, prompts, and generated outputs
- capture generation metadata for every image
- provide a simple way to review generated outputs
- document the model, approach, assumptions, limitations, and failure cases

## Customization Requirements

The solution should allow users to configure generation options such as:

- number of images to generate
- target species label
- age or growth stage
- season
- time of day
- lighting condition
- weather condition
- camera angle
- background variation
- leaf density
- tree health or visible stress condition
- image style realism level
- output image size
- random seed or reproducibility settings

Contributors may propose additional useful parameters.

## Suggested Approach

Contributors are free to propose their own approach.

Possible approaches may include:

- local diffusion models
- image-to-image generation
- prompt-to-image generation
- ControlNet-style conditioning
- fine-tuned or adapter-based local models
- locally hosted open image generation models
- optional provider adapters for hosted image generation services

The solution should explain why the selected model is suitable, what hardware is required, what can be generated reliably, and what should still be reviewed manually.

## Suggested Stack

Preferred languages:

- Python
- C#

Possible libraries and tools:

- PyTorch
- Hugging Face Diffusers
- ONNX Runtime
- OpenCV
- Pillow
- ComfyUI or similar local workflow tools
- ML.NET where applicable

Contributors may use other tools if they explain the reasoning.

## Data Access

Seed images are not included publicly in this repository unless they are open, synthetic, or approved for public use.

Contributors may use:

- open-license tree images
- contributor-created tree images
- approved seed image packs provided by the maintainers
- public-safe prompts and labels

Contributors who need access to seed images can contact the maintainers by email. Contact [abhijeet@366pitech.com]

Do not commit private geo-tagged images, precise location data, private farm or project data, credentials, model access tokens, or restricted-license imagery to the repository.


## Contribution Guidelines

- Fork the repository.
- Create a feature branch.
- Submit your contribution through a pull request.
- Keep the implementation focused on this challenge.
- Do not commit private images, precise location data, credentials, model tokens, or large generated datasets.
- Include setup and running instructions.
- Include sample output using safe, open, synthetic, or approved images and prompts.
- Explain your assumptions and known limitations.
- Mention any additional data you needed or data gaps you found.
- Document how the solution can be customized, secured, and scaled.
