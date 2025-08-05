# Service Dependencies and Integration Patterns

## Service Communication Matrix

| Service | User | Product | Order | Payment |
|---------|------|---------|-------|---------|
| **User** | - | Profile sync (async) | User validation (sync) | Account status (async) |
| **Product** | User preferences (async) | - | Inventory check (sync) | - |
| **Order** | User lookup (sync) | Product details (sync) | - | Payment processing (sync) |
| **Payment** | Account verification (sync) | - | Payment confirmation (async) | - |

## Integration Patterns

**Synchronous Communication (REST)**:
- User validation during order creation
- Product availability checks
- Payment authorization requests
- Data required for immediate business decisions

**Asynchronous Communication (Events)**:
- User profile updates → Product service for personalization
- Order status changes → User service for notifications  
- Payment confirmations → Order service for fulfillment
- Account status changes → cross-service coordination

## Event Schema

**User Events**:
```json
{
  "eventType": "UserProfileUpdated",
  "userId": "uuid",
  "timestamp": "ISO-8601",
  "changes": {"preferences": {...}}
}