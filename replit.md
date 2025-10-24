# HealthID Nexus - Decentralized Health Identity System

## Overview

HealthID Nexus is a blockchain-integrated system designed to provide secure, patient-owned medical records and streamline insurance claim management. It features emergency QR access, role-based dashboards for various healthcare stakeholders (patients, doctors, hospitals, emergency responders, insurance providers, administrators), and blockchain-verified insurance claims. The project aims to enhance data security, improve accessibility for authorized personnel, and provide a robust platform for managing health identities and claims.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript, using Vite for development and Wouter for routing.
- **UI/UX**: Shadcn/ui (built on Radix UI) for components, Tailwind CSS for styling, and Material Design principles. Features a custom color palette, Inter font, and responsive design with light/dark modes.
- **State Management**: TanStack Query (React Query) for server state management.

### Backend Architecture
- **Framework**: Express.js with TypeScript, following a RESTful API design.
- **Authentication**: Web3 wallet-based authentication (MetaMask via ethers.js) with wallet signature verification.
- **Authorization**: Role-Based Access Control (RBAC) across six distinct roles, with session management tied to wallet addresses.
- **Data Access**: Centralized storage abstraction interface using Drizzle ORM for type-safe PostgreSQL queries and transaction support.

### Data Storage
- **Database**: PostgreSQL (Neon serverless PostgreSQL in cloud) with connection pooling.
- **Schema Design**: Includes tables for users (wallet-based), KYC verification, health profiles, encrypted medical records (simulated IPFS CIDs), granular access control, treatment logs, insurance policies, claims processing, and audit logs.
- **Security**: Client-side encryption (CryptoJS) for sensitive data, simulated IPFS for immutability, SHA-256 hashing, and encrypted emergency QR data.

### Key Architectural Decisions
- **Wallet-Based Authentication**: Utilizes Web3 wallet signatures for strong, decentralized identity verification, eliminating password vulnerabilities.
- **Role-Based Dashboard System**: Provides distinct interfaces and data access for patients, doctors, hospitals, emergency personnel, insurance providers, and administrators, enforcing the principle of least privilege.
- **Simulated Blockchain Layer**: Employs CIDs, hashes, and transaction-like IDs to simulate blockchain verification, allowing for future integration with actual smart contracts.
- **Emergency QR Access**: Implements QR codes with encrypted critical medical information for instant, offline access by first responders.
- **Granular Access Control**: Manages fine-grained permissions (read/write/emergency) with expiration dates for medical records, aligning with privacy requirements.
- **Centralized Storage Abstraction**: Offers a single, type-safe interface for all database operations, improving maintainability and consistency.

## External Dependencies

- **Blockchain & Web3**: `ethers.js` (v6) for wallet connectivity and message signing, MetaMask as the primary wallet provider.
- **Database & ORM**: `@neondatabase/serverless` for PostgreSQL connection, Drizzle ORM, `drizzle-kit` for schema management, `connect-pg-simple` for session storage.
- **UI Component Libraries**: `@radix-ui/*` primitives, `react-day-picker`, `cmdk`, QR code generation libraries.
- **Utilities**: `crypto-js` for encryption, `date-fns` for date manipulation, `nanoid` for unique IDs, `class-variance-authority`, `clsx`, `tailwind-merge` for CSS.
- **Development Tools**: `tsx`, `esbuild`, `cross-env`.