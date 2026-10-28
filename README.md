# Pharmacio

**A smart pharmacy management system** for inventory, point of sale, purchasing workflows, and document processing—with web and mobile clients backed by a Django API and AI/OCR services.

## What it does

- Manages pharmacy inventory, stock alerts, and point-of-sale transactions.
- Supports purchase proposals and approval workflows.
- Provides web and mobile Flutter applications.
- Accepts pharmacy documents for asynchronous OCR processing and backend callbacks.
- Uses role-based access controls and audit logging.

## Architecture

```text
Flutter Web ─┐
             ├── Django REST API ── OCR/AI service
Flutter Mobile┘
```

The backend handles application data and workflows. It dispatches document-processing jobs to an OCR service and receives the results asynchronously. The two AI/OCR repositories below are kept as separate implementations; they are not both required to run the application. See the backend and service READMEs for configuration and integration details.

## Repository layout

| Component | Purpose | Source repository | Imported branch |
|---|---|---|---|
| [`backend/`](./backend/) | Django REST API, inventory, POS, purchasing, and access control | [pharmacio-backend](https://github.com/sharaffatima/pharmacio-backend) | `main` |
| [`mobile/`](./mobile/) | Flutter mobile client | [pharmacio-mobile](https://github.com/sharaffatima/pharmacio-mobile) | `dev` |
| [`web/`](./web/) | Flutter web client | [pharmacio-web](https://github.com/sharaffatima/pharmacio-web) | `main` |
| [`services/ocr/`](./services/ocr/) | FastAPI OCR service | [sharafAI-pharmacio-ocr](https://github.com/sharaffatima/sharafAI-pharmacio-ocr) | `main` |
| [`services/ai/`](./services/ai/) | AI/OCR service | [pharmacio-ai](https://github.com/sharaffatima/pharmacio-ai) | `main` |

## Getting started

Each component has its own dependencies and setup. Start with its README:

- [Backend setup](./backend/README.md) — Django, PostgreSQL, Redis, and Docker/local development instructions.
- [Mobile setup](./mobile/README.md) — Flutter and FVM instructions.
- [Web setup](./web/README.md) — Flutter web instructions.
- [OCR service setup](./services/ocr/README.md)
- [AI service setup](./services/ai/README.md)

There is not yet a root-level command that configures and starts the complete system. Configure the backend and the selected OCR service to use matching credentials and service URLs as described in their documentation. Local `.env` files are ignored; use the documented example files and provide your own values.

## Technologies

Django REST Framework · PostgreSQL · Redis/Celery · Flutter/Dart · FastAPI · OpenCV · EasyOCR

## Source history

The repositories were imported under their own directories with their commit histories retained. Exact `.env` files were removed from the imported history; example configuration files remain where provided. The source repositories are listed above for reference.
