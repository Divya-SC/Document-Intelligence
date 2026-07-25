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
