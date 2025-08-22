# VoxScript - Audio to Subtitle Converter

## Overview

VoxScript is a full-stack web application for converting audio files to subtitle files (SRT format). The application allows users to upload audio files (MP3, MP4, WAV, M4A), processes them through audio conversion and speech recognition, and generates downloadable SRT subtitle files. Built with a modern tech stack including React, Express, TypeScript, and Drizzle ORM.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript and Vite for fast development
- **UI Components**: Radix UI primitives with shadcn/ui component library
- **Styling**: Tailwind CSS with custom design system variables
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for lightweight client-side routing
- **File Upload**: React Dropzone for drag-and-drop file uploads

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **File Processing**: Multer for multipart file uploads with file type validation
- **Audio Processing**: FFmpeg for audio format conversion to 16kHz mono WAV
- **Speech Recognition**: Vosk speech recognition engine via Python subprocess
- **API Design**: RESTful endpoints for file upload, processing status, and download

### Data Storage Solutions
- **Database**: PostgreSQL with Drizzle ORM for type-safe database operations
- **Database Provider**: Neon Database (@neondatabase/serverless)
- **Schema Management**: Drizzle Kit for migrations and schema management
- **Storage Strategy**: In-memory storage implementation with interface for easy swapping
- **File Storage**: Local filesystem for uploaded files and generated SRT files

### Authentication and Authorization
- **Current State**: No authentication system implemented
- **Session Management**: Basic session setup with connect-pg-simple (not actively used)

### Processing Pipeline
1. **File Upload**: Validates file types and size limits (500MB max)
2. **Audio Conversion**: Uses FFmpeg to convert to 16kHz mono WAV format
3. **Speech Recognition**: Python script with Vosk model processes WAV file
4. **SRT Generation**: Converts recognition results to SRT subtitle format
5. **Status Tracking**: Real-time progress updates through polling mechanism

### Database Schema
- **audioFiles Table**: Stores file metadata, processing status, progress, and results
- **Status Types**: uploaded, converting, transcribing, completed, failed
- **Tracking Fields**: progress percentage, error messages, processing timestamps

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: PostgreSQL database connection
- **drizzle-orm & drizzle-kit**: Type-safe ORM and migration tools
- **@tanstack/react-query**: Server state management and caching
- **multer**: File upload handling middleware
- **fluent-ffmpeg**: Audio processing and format conversion

### UI and Styling
- **@radix-ui/***: Comprehensive set of UI primitives
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Component variant management
- **lucide-react**: Icon library

### Development Tools
- **vite**: Fast build tool and development server
- **tsx**: TypeScript execution for Node.js
- **wouter**: Lightweight React router

### Audio Processing Pipeline
- **FFmpeg**: External binary for audio format conversion
- **Vosk**: Python-based speech recognition engine
- **Python**: Required for running Vosk transcription scripts

### Build and Deployment
- **esbuild**: Fast JavaScript bundler for production builds
- **PostCSS**: CSS processing with Tailwind CSS