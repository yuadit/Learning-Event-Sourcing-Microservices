# Learning-Event-Sourcing-Microservices

# Order Service

## Entities

### Order
- `orderId` (Primary Key)
- `customerId`
- `status`
- `totalAmount`
- `createdAt`
- `updatedAt`

## Events

### OrderCreatedEvent
- `orderId`
- `customerId`
- `totalAmount`
- `createdAt`

### OrderApprovedEvent
- `orderId`
- `approvedAt`

### OrderShippedEvent
- `orderId`
- `shippedAt`

### OrderCancelledEvent
- `orderId`
- `cancelledAt`

## Repositories

### OrderRepository
- `SaveOrder(Order)`
- `FindOrderById(orderId)`
- `FindOrdersByCustomerId(customerId)`

## Services

### OrderCommandService
- `createOrder(orderDto)`
- `approveOrder(orderId)`
- `shipOrder(orderId)`
- `cancelOrder(orderId)`

### OrderQueryService
- `getOrder(orderId)`
- `getOrdersByCustomerId(customerId)`

# Customer Service

## Entities

### Customer
- `customerId` (Primary Key)
- `name`
- `email`
- `createdAt`
- `updatedAt`

## Events

### CustomerCreatedEvent
- `customerId`
- `name`
- `email`
- `createdAt`

## Repositories

### CustomerRepository
- `SaveCustomer(Customer)`
- `FindCustomerById(customerId)`

## Services

### CustomerCommandService
- `createCustomer(customerDto)`

### CustomerQueryService
- `getCustomer(customerId)`

# Shared Library

## Event Publisher
### EventProducer
- `publishEvent(Event)`

## Event Consumer
### EventConsumer
- `consumeEvent(Event)`

# Kafka Topics
- `order-events`
- `customer-events`

# Saga Orchestrator
### SagaOrchestratorService
- `orchestrateOrderSaga(orderDto)`

# CQRS Views

### OrderView
- `queryOrder(orderId)`
- `queryOrdersByCustomerId(customerId)`

# Dependencies
- Spring Boot
- Spring Data
- Kafka Client
- Lombok (for reducing boilerplate code)
- Junit (for testing)
