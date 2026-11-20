# pudu

_Protocol for Unified Data Utilities_

A Model Context Protocol (MCP) server for the [NAHPU](https://github.com/nahpu) ecosystem.

Pudu connects AI assistants to discover NAHPU features, troubleshoot issues, generate document templates, configure data exports, and interact with scientific data workflows using natural language.

## Etymology

Named after[pudu (_Pudu puda_)](https://www.mammaldiversity.org/taxon/1006305/), one of the world's smallest deer native to southern Chile and southwestern Argentina. Pudu follows the naming tradition of the NAHPU ecosystem.

## Overview

Pudu serves as an integration layer between MCP-compatible clients and the NAHPU ecosystem. It is designed to operate independently of the NAHPU application, providing access to tools and resources without requiring a running NAHPU installation.

Pudu does not provide its own large language model or depend on a specific AI provider.

## Features

Planned capabilities include:

- **Documentation** — Search NAHPU documentation, discover features, and retrieve usage instructions.
- **Issue tracking** — Search known issues, feature requests, release notes, and potential solutions.
- **Document templates** — Generate and validate specimen tags, labels, catalogs, and other collection documents.
- **Export presets** — Create reusable configurations for exporting collection data.
- **Print layouts** — Generate layouts for specimen labels and collection documents.
- **Data standards** — Retrieve field definitions, metadata schemas, and Darwin Core mappings.
- **Document rendering** — Preview generated templates using synthetic collection data.
- **Local data utilities** — Support future integrations with local NAHPU installations for data queries, validation, and collection management.

## Architecture

Pudu is designed as a standalone MCP server that reuses existing NAHPU libraries, schemas, and documentation wherever possible.

The proposed architecture consists of:

- An MCP server implemented in Rust.
- Shared computational libraries from the NAHPU ecosystem.
- Structured documentation and versioned schemas.
- GitHub integration for issues and release information.
- Remote Streamable HTTP and local stdio transports.

The remote server is intended to be stateless. Generated templates and configurations can be imported directly into NAHPU, preserving its offline-first architecture.

## MCP tools

The following tools are proposed for the initial implementation.

| Tool | Description |
|---|---|
| `search_docs` | Search NAHPU documentation. |
| `get_doc` | Retrieve a documentation page. |
| `search_issues` | Search known issues and feature requests. |
| `get_issue` | Retrieve issue details. |
| `get_releases` | Retrieve release information. |
| `list_template_fields` | Discover supported template fields. |
| `get_template_schema` | Retrieve a document template schema. |
| `list_templates` | Discover built-in document templates. |
| `create_template` | Generate a NAHPU-compatible document template. |
| `validate_template` | Validate a document template. |
| `create_export_preset` | Generate a record export preset. |
| `create_print_layout` | Generate a print layout preset. |
| `get_dwc_mapping` | Retrieve Darwin Core field mappings. |

Tool definitions and availability may change during development.

## Usage

Pudu is intended to support MCP-compatible clients, including AI assistants and development environments.

The proposed public MCP endpoint is:

`https://mcp.nahpu.app/mcp`

### Example requests

Once connected to Pudu, users will be able to make requests such as:

- Are there any known issues with importing specimen records in NAHPU?
- Create a mammal specimen tag with scientific name, field number, locality, collector, and collection date.
- Generate an export preset compatible with Darwin Core.
- Create a print layout for specimen labels on A4 paper.
- Validate this document template against the current NAHPU schema.
- Explain how to export tissue and preparation records.

Generated configurations are intended to be compatible with NAHPU's existing import and export workflows.

## Design principles

- **Interoperability** — Use open protocols and standardized data formats.
- **Independence** — Operate without requiring a running NAHPU installation.
- **Privacy** — Do not require access to private collection databases for public tools.
- **Reproducibility** — Generate portable, versioned, and validated configurations.
- **Compatibility** — Maintain consistency with NAHPU's data models and schemas.
- **Provider neutrality** — Support MCP-compatible clients regardless of their underlying AI models.
- **Offline-first** — Preserve the ability to manage collection data locally without relying on AI services.

## Roadmap

- [ ] Implement the core MCP server.
- [ ] Support documentation search and retrieval.
- [ ] Integrate GitHub issues and releases.
- [ ] Publish machine-readable schemas and field catalogs.
- [ ] Implement document template generation and validation.
- [ ] Support export and print layout presets.
- [ ] Implement document rendering and previews.
- [ ] Deploy the public MCP endpoint.
- [ ] Support local MCP installations.
- [ ] Explore collection data validation and quality control tools.

## Project status

Pudu is in early development. The architecture, tool definitions, and public service endpoints may change.

## Contributing

Contributions, feature requests, and discussions are welcome. Please use the GitHub issue tracker to report bugs, propose new MCP tools, or discuss improvements to the project.

## Acknowledgments

Pudu builds upon the [Model Context Protocol](https://modelcontextprotocol.io/) and the open-source libraries and tools developed within the NAHPU ecosystem.
