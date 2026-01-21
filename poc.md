# Galactic Smoothie Telemetry API

Welcome to the interstellar smoothie station! This page mixes narrative flavor with an OpenAPI spec that GitLab can render for quick previews and approvals.

## Table of Cosmic Contents

1. [Mission Brief](#mission-brief)
2. [API Highlights](#api-highlights)
3. [OpenAPI Specification](#openapi-specification)
4. [Test Flight Checklist](#test-flight-checklist)
5. [Changelog Comet Tail](#changelog-comet-tail)

## Mission Brief

The Galactic Smoothie Council wants a telemetry feed describing how asteroids of fruit are blended across spaceports. Product managers review this doc directly in GitLab’s markdown preview, so we include narrative context plus the underlying OpenAPI contract.

## API Highlights

- Built for asynchronous fleets of blenders orbiting smoothie moons.
- Supports **adaptive zesty boosts** via query params.
- Emits compliance metadata so ISO auditors can sip in peace.

## OpenAPI Specification

```yaml
openapi: 3.1.0
info:
  title: Galactic Smoothie Telemetry API
  version: 0.42.0
  description: |
    Live metrics for orbital blender pods stationed across the Citrus Belt.
servers:
  - url: https://api.milkyway-smoothies.example.com/v1
    description: Production wormhole
  - url: https://sandbox.milkyway-smoothies.example.com/v1
    description: Beta nebulas only
paths:
  /smoothies:
    get:
      summary: List current smoothie telemetry frames
      tags:
        - Smoothies
      parameters:
        - in: query
          name: flavor
          schema:
            type: string
          description: Filter by dominant flavor spiral.
        - in: query
          name: boosterLevel
          schema:
            type: integer
            minimum: 0
            maximum: 5
          description: Zesty booster intensity.
      responses:
        '200':
          description: Telemetry bundle produced.
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/SmoothieFrame'
  /smoothies/{frameId}:
    get:
      summary: Retrieve a single smoothie frame by ID
      tags:
        - Smoothies
      parameters:
        - in: path
          name: frameId
          required: true
          schema:
            type: string
        - in: header
          name: X-Orbital-Trace
          schema:
            type: string
          description: Optional trace token for audit comets.
      responses:
        '200':
          description: Single frame details.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/SmoothieFrame'
        '404':
          description: No such frame drifting in the void.
components:
  schemas:
    SmoothieFrame:
      type: object
      required:
        - id
        - flavor
        - viscosity
        - generatedAt
      properties:
        id:
          type: string
          example: frame-asteroid-9087
        flavor:
          type: string
          example: Cosmic Mango
        viscosity:
          type: number
          format: float
          example: 3.14
        boosters:
          type: array
          items:
            type: string
          example:
            - citrus-zing
            - stardust-protein
        generatedAt:
          type: string
          format: date-time
          example: 2024-05-21T13:37:00Z
```

## Test Flight Checklist

- [ ] Validate the spec with Spectral.
- [ ] Simulate booster spikes using Postman or Bruno.
- [ ] Capture ISO 27005 risk delta for new flavors.

## Changelog Comet Tail

| Date | Version | Stardust Notes |
| --- | --- | --- |
| 2024-05-21 | 0.42.0 | Added boosterLevel query parameter and path tracing header. |
| 2024-04-08 | 0.30.0 | Introduced SmoothieFrame schema definition. |
| 2024-02-19 | 0.12.0 | First public warp toward GitLab preview compliance. |
