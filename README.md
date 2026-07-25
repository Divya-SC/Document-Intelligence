Document Intelligence

AI-powered document classification, metadata extraction, duplicate detection, and intelligent organization for enterprise documents using Google Apps Script and Google Drive.

Overview

Managing company documents across multiple legal entities quickly becomes difficult as files accumulate over time. Documents are often stored with inconsistent names, duplicated across folders, missing metadata, or placed in incorrect locations. This makes onboarding, audits, compliance reviews, and day-to-day operations more time-consuming than they need to be.

Document Intelligence is an AI-powered document management solution that automatically analyses uploaded documents, identifies the company and document type, extracts key metadata, detects duplicates and document versions, applies standardized naming conventions, and organizes files into a structured Google Drive folder hierarchy.

Rather than acting as simple file storage, the platform applies business rules and AI-assisted classification to create a consistent, searchable, and maintainable document repository suitable for organizations managing multiple legal entities.

Key Features
AI-powered document classification
Automatic metadata extraction
Company and entity identification
Intelligent document renaming
Duplicate detection using file hashing
Document version detection
Automated Google Drive folder organization
Personal KYC document workflow
Manual review workflow for uncertain documents
Processing logs and audit trail
Configurable business rules and folder mappings
Google Apps Script + Google Drive native implementation

How It Works

Document Intelligence follows a structured processing pipeline to classify, validate, and organize documents automatically.

                Upload Documents
                       │
                       ▼
            00_Migration Folder
                       │
                       ▼
          Process Migration Folder
                       │
                       ▼
          Duplicate Detection (SHA-256)
                       │
             ┌─────────┴─────────┐
             │                   │
       Duplicate Found       New Document
             │                   │
             ▼                   ▼
      Duplicate Review      AI Document Analysis
                                 │
                                 ▼
                     Metadata Extraction
                                 │
                                 ▼
                    Business Rule Validation
                                 │
                                 ▼
                 Folder & Filename Assignment
                                 │
                ┌────────────────┴────────────────┐
                │                                 │
                ▼                                 ▼
       Organized Documents              Needs Review
                │
                ▼
         Document Register
                │
        ┌───────┴────────┐
        ▼                ▼
  KYC Review      Processing Log
Processing Workflow

Every document uploaded into the migration folder follows the same workflow.

1. Duplicate Detection

Each file is hashed using SHA-256 before any AI processing begins.

If an identical document already exists, the file is registered in the Duplicate Review register and excluded from further processing.

2. AI Document Analysis

The AI analyses the document to identify:

Company or legal entity
Document scope (Corporate or Personal KYC)
Document type
Document category
Issue date
Expiry date
Recommended filename
Confidence score
3. Metadata Validation

Extracted information is validated against business rules.

Examples include:

Company name present
Valid document type
Valid category
Valid date formats
Required metadata
4. Intelligent Classification

The system determines:

Appropriate company folder
Document category
Review requirements
Version status
Processing outcome
5. Automatic Organization

Documents are automatically:

Renamed using standardized naming conventions
Moved into the correct Google Drive folder
Registered in the Document Register
Added to KYC Review or Document Review where applicable
Logged in the Processing Log

Core Features
AI-Powered Document Classification

Instead of relying on filenames or predefined rules alone, Document Intelligence analyses the document contents to identify key information.

The AI extracts:

Company or legal entity
Document scope (Corporate or Personal KYC)
Document type
Document category
Issue date
Expiry date
Standardized filename
Confidence score

This enables consistent document classification even when uploaded files have inconsistent or non-descriptive names.

Intelligent Document Organization

Once a document has been classified, the system automatically applies business rules to determine where it belongs.

The platform:

Creates company folders automatically when required.
Organizes documents into standardized category folders.
Applies consistent naming conventions.
Separates corporate documents from personal KYC records.
Routes documents requiring manual review to dedicated review workflows.
Duplicate Detection

Every document is fingerprinted using a SHA-256 hash before processing begins.

When an identical document already exists, the system:

Detects the duplicate before AI analysis.
Registers the duplicate in the Duplicate Review register.
Preserves the original document.
Prevents duplicate processing.

This reduces unnecessary AI requests and helps maintain a clean document repository.

Document Version Management

The platform compares newly uploaded documents against existing records to identify document versions.

It can distinguish between:

New documents
Updated versions
Older versions
Potential duplicates

This helps maintain a single source of truth while preserving document history.

Metadata Validation

Extracted information is validated before documents are organized.

Validation includes:

Company identification
Document type verification
Category verification
Date validation
Filename validation

Documents that fail validation are automatically routed for manual review.

Review Workflows

Not every document can be classified with complete certainty.

When required, the platform routes documents into dedicated review workflows, allowing users to validate metadata, correct classifications, and approve documents before they become part of the organized repository.

Current review workflows include:

Document Review
KYC Review
Duplicate Review

This balances automation with human oversight for exceptional cases.

Audit Trail and Processing Logs

Every processing action is recorded to provide a complete audit trail.

The system logs:

Processing date and time
File information
Processing status
Workflow outcome
Destination folder
AI processing results

This improves traceability and supports operational reviews and troubleshooting.

Architecture

Document Intelligence is built as a modular system where each component is responsible for a specific stage of the document lifecycle. This modular approach simplifies maintenance, allows new features to be added independently, and keeps the processing workflow scalable.

                     Google Drive
                          │
                          ▼
                00_Migration Folder
                          │
                          ▼
                 Migration Engine
                          │
          ┌───────────────┴───────────────┐
          ▼                               ▼
  Duplicate Detection               AI Analysis
          │                               │
          └───────────────┬───────────────┘
                          ▼
                  Metadata Validation
                          │
                          ▼
                 Classification Engine
                          │
                          ▼
                Folder Management Engine
                          │
                          ▼
          Google Drive Document Repository
                          │
          ┌───────────────┼───────────────┐
          ▼               ▼               ▼
 Document Register   Review Queues   Processing Log
System Components
Migration Engine

The Migration Engine is the entry point of the platform. It scans the migration folder, processes documents in configurable batches, and safely manages execution within Google Apps Script runtime limits.

Its responsibilities include:

Reading files from the migration folder
Batch processing
Runtime protection
Progress reporting
Error handling
AI Analysis Engine

The AI Analysis Engine examines each document and extracts structured metadata.

It identifies:

Company name
Document scope
Document type
Document category
Issue date
Expiry date
Standardized filename
Confidence score

The platform supports multiple AI providers, allowing fallback processing when the primary provider is unavailable.

Validation Engine

The Validation Engine verifies the extracted metadata before any document is organized.

Validation includes:

Required fields
Date formats
Category validation
Filename validation
Business rule checks

This prevents incomplete or inconsistent information from entering the document repository.

Classification Engine

The Classification Engine combines AI results with business rules to determine how each document should be processed.

It decides:

Processing status
Review requirements
Duplicate handling
Version handling
Document routing

This separates AI extraction from business decision-making.

Folder Management Engine

The Folder Management Engine maintains a consistent folder structure within Google Drive.

Its responsibilities include:

Creating company folders
Creating category folders
Renaming documents
Moving files
Maintaining standardized storage
Register Engine

Every processed document is recorded to provide traceability and operational visibility.

Current registers include:

Document Register
Duplicate Review
Document Review
KYC Review
Processing Log

These registers provide both an operational dashboard and an audit trail for document processing.

Design Principles

The platform is designed around a few core principles:

Automation first – reduce repetitive manual document handling.
Human oversight when needed – uncertain or exceptional cases are routed for review rather than guessed.
Modular architecture – each component has a single responsibility, making the system easier to maintain and extend.
Standardization – consistent naming, folder structures, and metadata improve document quality across entities.
Auditability – every significant processing action is recorded to support troubleshooting and governance.

Project Structure

The project is organized into independent modules, with each script responsible for a specific part of the document processing lifecycle. This modular design improves maintainability, simplifies testing, and allows new functionality to be added without affecting the rest of the system.

document-intelligence/
│
├── README.md
├── CHANGELOG.md
├── ROADMAP.md
├── LICENSE
├── .gitignore
│
├── src/
│   ├── Migration.gs
│   ├── Document_Processor.gs
│   ├── Gemini.gs
│   ├── OpenRouter.gs
│   ├── Duplicate_Manager.gs
│   ├── Folder_Manager.gs
│   ├── Register_Manager.gs
│   ├── Configuration.gs
│   ├── Utilities.gs
│   └── Logger.gs
│
├── docs/
│   ├── Architecture.md
│   ├── Installation.md
│   ├── Workflow.md
│   ├── Configuration.md
│   └── Screenshots/
│
└── examples/
    ├── Sample Configuration.xlsx
    └── Sample Folder Structure/
Source Code Overview
Migration.gs

The entry point of the application.

Responsible for:

Processing the migration folder
Managing processing batches
Runtime protection
Progress reporting
Recovery from interruptions
Document_Processor.gs

Coordinates the complete document processing workflow.

Responsibilities include:

Reading documents
Calling the AI engine
Executing validation
Determining processing status
Triggering folder organization
Updating registers

This acts as the orchestration layer of the application.

Gemini.gs

Integrates with Google's Gemini API for document intelligence.

Capabilities include:

Document classification
Metadata extraction
Company identification
Document type recognition
Filename generation
Confidence scoring

The design also supports provider replacement without affecting the rest of the system.

OpenRouter.gs

Provides AI provider failover.

If the primary AI provider becomes unavailable or reaches quota limits, the platform can automatically retry requests through an alternative provider.

This improves reliability during large migration jobs.

Duplicate_Manager.gs

Handles document fingerprinting and duplicate management.

Responsibilities:

SHA-256 hashing
Duplicate comparison
Duplicate registration
Duplicate review workflow
Folder_Manager.gs

Responsible for maintaining the Google Drive repository.

Functions include:

Company folder creation
Category folder creation
File movement
Standardized filenames
Folder mapping
Register_Manager.gs

Maintains all operational registers.

Current registers include:

Document Register
Processing Log
Duplicate Review
Document Review
KYC Review

These registers provide operational visibility and support audit requirements.

Configuration.gs

Centralizes configurable settings for the application.

Examples include:

AI provider selection
Confidence thresholds
Batch sizes
Folder IDs
Naming conventions
Business rules

Keeping configuration separate from processing logic allows the platform to be adapted without modifying core code.

Utilities.gs

Provides shared helper functions used throughout the project.

Examples:

Date formatting
String normalization
Filename cleanup
Common validation
Helper methods
Logger.gs

Records system events, processing outcomes, warnings, and errors.

Logging is separated from business logic to simplify troubleshooting and support future monitoring enhancements.

Design Philosophy

The project follows a modular architecture where each component has a clearly defined responsibility.

Rather than creating one large script that performs every task, the platform separates responsibilities into focused modules. This approach provides several benefits:

Easier maintenance and debugging
Improved readability
Independent testing of components
Simpler feature development
Better scalability as the project grows

As new capabilities—such as OCR, additional AI providers, document expiry monitoring, or approval workflows—are introduced, they can be added as new modules with minimal impact on the existing codebase.

Business Use Cases

Document Intelligence is designed for organizations that manage large volumes of structured documents across multiple legal entities. While the platform originated from solving corporate onboarding and compliance challenges, its architecture is applicable to a wide range of document-intensive business processes.

Corporate Document Management

Maintain a centralized repository of corporate records across multiple jurisdictions with consistent folder structures, standardized filenames, and searchable metadata.

Typical documents include:

Certificate of Incorporation
Memorandum & Articles of Association
Share Registers
Board Resolutions
Certificates of Good Standing
Annual Returns
Regulatory Filings
Banking & Financial Institution Onboarding

Support banking and payment institution onboarding by organizing entity documentation and ensuring required documents are readily available.

Examples include:

KYB packages
FATCA & CRS forms
AML Questionnaires
Banking Resolutions
Signatory Documents
Ownership Structures
Financial Institution Requests
Compliance & KYC Operations

Simplify compliance operations by organizing customer and corporate documentation into standardized review workflows.

Suitable for:

Corporate KYC
Customer Due Diligence (CDD)
Enhanced Due Diligence (EDD)
UBO Documentation
Periodic Reviews
Compliance Refresh Projects
Multi-Entity Organizations

Organizations operating across multiple companies often struggle with inconsistent document storage.

The platform automatically separates documents by:

Legal Entity
Jurisdiction
Document Category
Corporate Records
Personal KYC Records

This reduces manual sorting and improves document retrieval.

Audit Preparation

Preparing for internal or external audits often requires locating documents from different systems and folders.

Document Intelligence provides:

Standardized document naming
Complete processing history
Centralized registers
Structured storage
Traceable document movement

This helps reduce preparation time and improves audit readiness.

Digital Document Migration

Many organizations have years of legacy documents stored in shared drives with inconsistent naming and folder structures.

The migration workflow allows these repositories to be analyzed, classified, and reorganized into a standardized document library without manually reviewing every file.

Operational Knowledge Management

Beyond compliance, the platform can be adapted to organize operational documents such as:

Policies and Procedures
Contracts
Vendor Documentation
Internal Guidelines
Project Documentation
Financial Records

The AI classification engine and business rules can be extended to support additional document types as organizational needs evolve.

Who Can Benefit?

Document Intelligence is suitable for organizations and teams that rely on accurate, well-organized documentation, including:

Financial Institutions
FinTech Companies
Payment Service Providers (PSPs)
Electronic Money Institutions (EMIs)
Corporate Services Providers
Legal Teams
Compliance Teams
Finance Teams
Internal Audit Functions
Operations Teams
Multi-Entity Corporate Groups
Real-World Problem

Many organizations still receive documents through email, cloud storage, or shared folders. Teams spend considerable time identifying document types, renaming files, creating folders, checking for duplicates, and ensuring documents are stored consistently.

Document Intelligence automates these repetitive tasks while preserving human oversight for exceptional cases. By combining AI-assisted classification with configurable business rules, it reduces manual effort, improves consistency, and creates a structured repository that supports onboarding, compliance, audits, and day-to-day operations.

Engineering Challenges & Lessons Learned

Building Document Intelligence involved more than integrating AI into a document workflow. The project required balancing automation, reliability, and operational accuracy while working within the constraints of Google Apps Script and external AI services.

Challenge 1: AI Reliability

Large language models can occasionally produce inconsistent or incomplete metadata. Relying solely on AI responses would result in misplaced documents and unreliable classifications.

Solution

Business rule validation after AI extraction
Confidence scoring
Manual review workflows
Fallback processing for uncertain results

Outcome

AI provides recommendations, while business rules determine the final processing outcome.

Challenge 2: Duplicate Documents

Organizations often store multiple copies of the same document under different filenames.

Examples:

Board Resolution.pdf
Board Resolution Final.pdf
Board Resolution FINAL V2.pdf
Resolution Signed.pdf

Traditional filename comparisons cannot reliably detect these duplicates.

Solution

Every document is fingerprinted using a SHA-256 hash before processing.

Outcome

Reliable duplicate detection
Reduced storage duplication
Lower AI processing costs
Cleaner document repository
Challenge 3: Processing Large Document Libraries

Google Apps Script has execution time limits, making it impractical to process thousands of documents in a single run.

Solution

Configurable batch processing
Runtime protection
Progress tracking
Resume processing from the remaining queue

Outcome

Large migrations can be completed across multiple executions without restarting from the beginning.

Challenge 4: AI Service Availability

AI providers may experience quota limits, temporary outages, or API changes.

Solution

The platform separates the AI integration layer from the processing engine, allowing alternative providers to be used without redesigning the workflow.

Outcome

Greater resilience and flexibility as AI services evolve.

Challenge 5: Standardization

Documents received from different jurisdictions, banks, and service providers rarely follow consistent naming conventions or folder structures.

Solution

Standardized filenames
Configurable folder mappings
Business rule validation
Consistent metadata model

Outcome

A structured repository that is easier to search, review, and maintain.

Technical Stack
Component	Technology
Language	JavaScript (Google Apps Script)
Platform	Google Workspace
Storage	Google Drive
Database	Google Sheets
AI Providers	Google Gemini, OpenRouter
Hashing	SHA-256
Version Control	Git & GitHub
Repository Goals

This project is intended to demonstrate practical software engineering applied to business operations.

The focus is on building solutions that:

Automate repetitive document handling tasks
Improve consistency and data quality
Support compliance and operational processes
Combine AI with deterministic business rules
Remain maintainable through modular architecture

The repository is actively maintained and evolves through incremental improvements, with each version introducing new capabilities while preserving a stable processing foundation.

Contributing

Contributions, suggestions, and discussions are welcome.

If you identify an issue or have an idea for improving the platform:

Open an issue describing the problem or enhancement.
Discuss the proposed solution.
Submit a pull request with clear documentation and testing notes.

Please keep changes modular and aligned with the project's design principles.

License

This project is released under the MIT License. See the LICENSE file for details.

A final suggestion

One thing I would add that most GitHub repositories don't have is a Project Evolution timeline. It tells the story of how the idea developed, which is especially valuable in a portfolio repository.

2026
│
├── Idea
│   Manual document organization was consuming significant operational time.
│
├── Version 1
│   AI classification and automated document organization.
│
├── Version 2
│   Duplicate detection, processing engine, and review workflows.
│
├── Version 3
│   Operational intelligence, expiry monitoring, and compliance dashboards.
│
└── Future
    Enterprise document intelligence platform.
