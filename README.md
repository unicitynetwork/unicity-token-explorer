# Technical Task: Unicity Explorer Application

## Project Overview

Unicity Explorer is a stand-alone web application for managing TXF (Transaction Flow) tokens within the Unicity ecosystem. The application will provide a complete interface for users to view, manage, transfer, and receive tokens while connecting to the Unicity aggregator network.

This technical task outlines the requirements for UX/GUI developers to implement the application based on the existing TXF SDK.

## Application Architecture

The application will follow a modular architecture with the following main components:

1. **Core Engine Integration**: Integration with the tx-flow-engine for token operations
2. **UI Framework**: Modern web framework implementation with responsive design
3. **Storage Providers**: Connectors for various storage solutions
4. **Transport Connectors**: Integration with messaging and file transfer services
5. **Authentication System**: Secure management of user secrets

## UI Layout & Components

The UI will consist of three main panels:

### Left Panel (Provider Management)
- Storage provider selection and configuration
- Transport connector selection and configuration
- List of active/configured providers
- Provider status indicators
- Add/remove provider controls

### Top Panel (User & Network Configuration)
- Secret management interface (add, remove, view)
- Derived recipient addresses display
- Unicity aggregator network URL configuration
- Nametag token management interface
  - Create new nametags
  - Manage existing nametags
  - Name-to-pubkey translation configuration

### Central Panel (Token Explorer)
- File browser interface for TXF files/objects
- Folder structure navigation
- Token summary cards showing:
  - Token type
  - Token value
  - Token status (spendable, spent, not owned)
  - Token class
  - Token ID (abbreviated)
- Context menu for token operations:
  - Send
  - Import
  - Export
  - Move
  - Share
  - Delete
- Drag and drop functionality
- Import/Export buttons for external storage
- "Quarantine" folder for newly received tokens
- Notification system for incoming tokens

### Right Panel (Summary & Operations)
- Total balance for each fungible token type
- Number of NFTs by token class
- Token sending interface
  - Recipient address input (supporting pubkey, pointer, and nametag formats)
  - Token selection
  - Transport method selection
  - Send button
- Quick action buttons
- Token operation status and history

## Functional Requirements

### 1. User Secret Management
- Secure storage of user secrets (client-side encryption)
- Interface to add, remove, and manage secrets
- Automatic derivation and display of recipient addresses from secrets
- Option to name/label each secret
- Secret strength indicator

### 2. Storage Provider Integration
- Support for multiple storage providers:
  - Local filesystem folder
  - IPFS integration
  - YJS-based decentralized storage
  - Google Drive
  - Dropbox
  - OneDrive
  - Others as specified
- Interface to add/configure storage providers
- Storage quota and usage display
- Auto-sync functionality
- Storage preference configuration

### 3. Token Management
- Display tokens in a file browser interface
- Group tokens by folder/category
- Show token metadata and status
- Support for token operations:
  - Creating new tokens (minting)
  - Sending tokens to recipients
  - Receiving tokens from senders
  - Importing token transaction flows
  - Exporting token transaction flows
  - Moving tokens between folders
- Batch operations on multiple tokens

### 4. Transport Connector Integration
- Support for multiple transport methods:
  - Email
  - Telegram
  - Tawasal
  - Viber
  - WhatsApp
  - Discord
  - YJS real-time collaboration
  - Others as specified
- Interface to configure transport connectors
- Status indicators for transport connectivity
- Transaction history by transport method

### 5. Quarantine & Notification System
- Dedicated "quarantine" folder for incoming tokens
- Notification system for new token arrivals
- Token review interface
- Approval/rejection mechanism
- Auto-import option for trusted senders

### 6. Token Scanning & Auto-Import
- Periodic background scanning of token storage
- Automatic attempt to import transactions using available secrets
- Progress indication for background operations
- Scan frequency configuration
- Manual scan trigger

### 7. Network Configuration
- Interface to manage Unicity aggregator gateway URLs
- Network status indicators
- Connection testing functionality
- Gateway performance metrics

### 8. Nametag Token Management
- Interface to create and manage nametag tokens
- Name-to-pubkey translation configuration
- Nametag search and lookup functionality
- Nametag sharing options

## Technical Requirements

### Frontend Implementation

1. **Framework & Technologies**
   - JavaScript-based implementation
   - Modern web framework (React, Vue, or similar)
   - Responsive design supporting desktop and tablet views
   - CSS styling with a consistent design system
   - Webpack or similar for bundling

2. **TXF SDK Integration**
   - Full integration with tx-flow-engine SDK
   - Proper error handling for all SDK operations
   - Consistent state management for token operations

3. **Browser Compatibility**
   - Support for modern browsers (Chrome, Firefox, Safari, Edge)
   - Progressive enhancement for older browsers where possible
   - Responsive design for various screen sizes

4. **Security Measures**
   - Client-side encryption for sensitive data
   - No transmission of secrets to servers
   - Secure connection handling
   - XSS protection
   - Input validation
   - Proper error handling to prevent information leakage

5. **Performance Optimization**
   - Efficient rendering of token lists
   - Pagination for large token collections
   - Lazy loading of token data
   - Caching of frequently accessed data
   - Background processing for intensive operations

### Storage Provider Implementation

1. **Common Interface**
   - Abstract provider interface for all storage types
   - Standardized error handling
   - Progress reporting for file operations

2. **Provider-Specific Implementation**
   - Local filesystem integration using File System Access API
   - IPFS connector using appropriate JavaScript library
   - YJS connector for real-time collaborative storage
   - OAuth integration for Google Drive, Dropbox, OneDrive
   - Proper credential management for cloud services

3. **Synchronization**
   - Conflict resolution strategies
   - Background synchronization
   - Manual sync trigger
   - Sync status indication

### Transport Connector Implementation

1. **Common Interface**
   - Abstract connector interface for all transport types
   - Standardized message format
   - Delivery status tracking

2. **Connector-Specific Implementation**
   - Email connector using appropriate APIs
   - Telegram bot integration
   - Integration with other messaging platforms
   - YJS-based real-time transport
   - Proper credential management

## P2P Components (YJS-based)

1. **P2P Storage Provider**
   - YJS document structure design
   - Peer discovery mechanism
   - Conflict resolution strategy
   - Data persistence strategy

2. **P2P Transport Provider**
   - YJS awareness protocol utilization
   - Direct peer messaging
   - Offline message handling
   - Connection state management

## UI/UX Guidelines

1. **General Principles**
   - Clear, consistent layout
   - Intuitive navigation
   - Responsive design
   - Accessibility compliance (WCAG 2.1 AA)
   - Consistent color scheme and typography

2. **Token Representation**
   - Clear visual distinction between token states
   - Consistent token card design
   - Important information prominence
   - Hover states for additional information

3. **Operation Feedback**
   - Clear loading indicators
   - Success/error notifications
   - Operation progress bars
   - Confirmation dialogs for destructive actions

4. **Contextual Help**
   - Tooltips for complex features
   - Onboarding guides for new users
   - Contextual help documentation
   - Keyboard shortcut reference

## Development Approach

1. **Component-Based Development**
   - Modular implementation of UI components
   - Reusable component library
   - Component documentation

2. **State Management**
   - Consistent application state handling
   - Predictable data flow
   - Proper token operation state tracking

3. **Testing Strategy**
   - Unit tests for components
   - Integration tests for token operations
   - UI testing for critical workflows
   - Performance testing

4. **Documentation**
   - Code documentation
   - API references
   - User documentation
   - Developer guides

## Implementation Phases

### Phase 1: Core Framework & Basic UI
- Application structure setup
- Basic UI layout implementation
- Token display and navigation
- Integration with tx-flow-engine SDK
- Local storage provider

### Phase 2: Enhanced Token Management
- Token operation implementations
- Context menu functionality
- Token status visualization
- Token filtering and search
- Basic transport connector (local/file)

### Phase 3: Provider Integration
- Cloud storage providers
- Additional transport connectors
- Network configuration
- Quarantine system
- Notification system

### Phase 4: Advanced Features
- Nametag management
- Auto-import functionality
- Background scanning
- Batch operations
- YJS-based p2p components

### Phase 5: Polish & Optimization
- Performance optimization
- UI refinement
- Accessibility improvements
- Browser compatibility testing
- Documentation completion

## Mockups and Design Assets

The implementation should follow the design direction indicated in the "Unicity Explorer.pdf" sketch, with additional elements as described in this technical task. Detailed mockups will be provided for:

1. Complete application layout with all panels
2. Token card design
3. Provider configuration interfaces
4. Token operation flows
5. Notification and quarantine system

## Technical Integration Points

### TXF SDK Integration
The application will utilize the following SDK functions:
- `mint`: For token creation
- `createTx`: For sending tokens
- `importTx`: For receiving tokens
- `exportFlow`: For exporting tokens
- `importFlow`: For importing tokens
- `getTokenStatus`: For checking token status
- `collectTokens`: For scanning and filtering tokens
- `calculatePointer`: For generating recipient pointers

### Communication with Unicity Aggregator
- RESTful API communication with configurable endpoints
- Proper error handling for network issues
- Retry mechanisms for failed operations
- Request rate limiting

## Deliverables

1. **Source Code**
   - Complete application source code
   - Build configuration
   - Dependency documentation

2. **Documentation**
   - Technical documentation
   - Code documentation
   - User manual
   - API references

3. **Build Artifacts**
   - Production-ready build
   - Development build
   - Test reports

4. **Design Assets**
   - UI component library
   - Icon set
   - Style guide

## Acceptance Criteria

The implementation will be considered complete when:

1. All functional requirements are implemented
2. The application successfully integrates with the tx-flow-engine SDK
3. All storage providers and transport connectors function correctly
4. The UI is responsive and follows the design guidelines
5. The application passes all specified tests
6. Documentation is complete and accurate

## Technical Constraints

1. Browser compatibility with Chrome, Firefox, Safari, Edge (latest 2 versions)
2. Client-side only implementation (no server-side components except APIs)
3. Compliance with modern web security practices
4. Integration with specified third-party services and APIs

## Additional Considerations

1. **Internationalization**
   - Support for multiple languages
   - RTL layout support
   - Localized date and number formats

2. **Offline Support**
   - Basic functionality when offline
   - Queue operations for when connection is restored
   - Clear indication of offline status

3. **Future Extensibility**
   - Plugin architecture for additional providers
   - Extensible token visualization
   - API for potential integrations
