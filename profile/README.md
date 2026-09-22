
# Medol Labs

Medol Labs builds open-source tools for spec-driven, event-modeling-based application development.

Medol starts from an explicit domain specification instead of ad-hoc prompts, screens, or database tables. A Medol model describes contexts, commands, events, read models, policies, deployments, and simulations, then generates runnable software artifacts from that shared model.

## What Is Medol?

Medol is a modeling and code generation toolkit for building business systems from executable domain specifications.

It helps teams move from:

```text
Domain Specification
  -> Semantic Codegen Model
  -> Backend Services
  -> Frontend Consoles
  -> Operations Assets
  -> Simulation Scenarios
  -> Living Documentation
```

Medol is designed for systems where business behavior, event flow, read models, deployment topology, and test scenarios should stay aligned over time.

## Spec-Driven Development

AI coding has made software creation faster, but it also exposes a hard problem: natural-language prompts are often ambiguous, incomplete, and difficult to keep consistent as a system grows.

This is especially visible in vibe coding workflows. They are great for quick exploration, but production systems need more than momentum. They need stable intent, repeatable generation, testable behavior, and a shared source of truth.

Medol approaches this through spec-driven development.

A Medol model acts as a durable specification for the system. It captures business behavior in a structured form that both humans and generators can understand:

- Commands describe user intent
- Events describe business facts
- Read models describe operational views
- Policies and processors describe automation
- Deployments describe runtime packaging
- Simulations describe executable business flows

This helps solve several common AI programming problems:

- **Prompt drift**: implementation decisions are anchored to a model, not scattered across chat history.
- **Inconsistent code**: repeated patterns are generated from the same semantic source.
- **Lost business intent**: domain behavior remains visible as commands, events, policies, and scenarios.
- **Regeneration risk**: generated and hand-written code have explicit boundaries.
- **Testing gaps**: scenarios and simulation data can be derived from the same specification.
- **Documentation decay**: docs can be regenerated from the model as the system evolves.

Medol does not replace developers or AI assistants. It gives them a stronger operating surface: a specification that can be reviewed, versioned, generated, tested, and evolved.

## Projects

### `medol`

The Medol modeling tool and DSL.

It provides:

- MEDOL domain modeling language
- Event-modeling-oriented syntax
- Model validation
- Codegen model export
- Documentation export
- Built-in reusable domain models such as identity access management

### `medol-codegen`

The Medol code generator.

It generates application artifacts from `codegen-model.json`, including:

- Axon 5 / Spring Boot backend services
- Refine / React frontend consoles
- Docker Compose and Kubernetes/K3s operations assets
- Simulation services and deterministic test flows
- Shared project scaffolding and runtime conventions

### `federation-learning`

A reference example system built with Medol.

It demonstrates a federated learning platform with:

- Platform-side federation and training orchestration
- Runtime-agent-side dataset validation and local execution
- Runtime engine integration
- Runtime infrastructure deployment through Docker Compose and K3s
- Generated backend, frontend, operations, and simulation-oriented workflows

## Why Medol?

Most application generators start from CRUD resources or UI forms. Medol starts from business behavior.

That means generated systems can preserve the intent of the specification:

- Commands express user intent
- Events capture business facts
- Read models support operational views
- Policies and processors express automation
- Deployments describe how contexts are packaged
- Simulations exercise real business flows

The goal is not just to generate code once, but to keep model, implementation, documentation, operations, and test data moving together.

## Design Principles

- **Spec first**: domain behavior is the source of truth.
- **Generated but extensible**: generated code has clear boundaries for hand-written adapters and domain overrides.
- **Runtime aware**: deployment and infrastructure are part of the model.
- **Simulation friendly**: generated systems should be easy to seed, test, and rehearse.
- **AI compatible**: AI assistants work better when they operate against explicit, versioned specifications.
- **Open by default**: Medol should be understandable, scriptable, and useful without a hosted platform.

## Current Status

Medol is under active development.

The current focus areas are:

- Stabilizing the MEDOL DSL
- Improving Axon 5 and Refine generation
- Strengthening operations generation for Docker Compose and K3s
- Building better simulation and realistic test-data tooling
- Preparing the Federation Learning example as a complete reference implementation

## Getting Started

Build the Medol codegen image first:

```bash
git clone https://github.com/medol-labs/medol-codegen.git
cd medol-codegen
docker build -f Dockerfile.codegen -t medol-codegen .
```

Start Medol and create your domain model.

Then create an empty workspace directory for generated artifacts:

```bash
mkdir -p my-medol-workspace
cd my-medol-workspace
```

Run the codegen container with the workspace mounted:

```bash
docker run --rm -it \
  -v "$PWD:/workspace" \
  medol-codegen
```

Inside the container, run `update` to generate or refresh `codegen-model.json`:

```bash
update
```
update pulls the current model from the running local Medol service and writes codegen-model.json into the mounted workspace. Make sure the Medol service is running on your machine before executing this command.
update also creates the Medol workspace metadata when needed, including:

```text
.medol/
  source.medol
  codegen-model.json
```

Then run generators from the container default directory, `/workspace`:

```bash
gen
```

The generator runs interactively. Select the target project, generator type, and slices you want to generate from the prompts.

## Repositories

- `medol` - modeling language, editor, validators, and exporters
- `medol-codegen` - code generation targets and templates
- `federation-learning` - end-to-end example system

## License

Medol Labs projects are intended to be open source. See each repository for its license.

## Community

Medol Labs is exploring how domain modeling, event modeling, code generation, simulation, and AI-assisted development can work together as a practical software delivery workflow.

If you are interested in spec-driven development, event sourcing, domain-driven design, generated applications, or simulation-based testing, welcome to follow along.

