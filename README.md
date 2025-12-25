# E-Commerce Microservices - Configuration Repository

Ce repository contient toutes les configurations centralisées pour l'application E-Commerce basée sur une architecture microservices.

## 📁 Structure

```
config-repo/
├── application.properties          # Configuration commune à tous les services
├── eureka-server.properties        # Configuration Eureka Server
├── gateway-service.properties      # Configuration API Gateway
├── product-service.properties      # Configuration Product Service
├── order-service.properties        # Configuration Order Service (avec propriété personnalisée)
├── client-api.properties           # Configuration Client API (JWT + Email)
└── frontend-service.properties     # Configuration Frontend Thymeleaf
```

## 🔧 Configurations Clés

### Propriété Personnalisée
- **`mes-config-ms.commandes-last=10`** dans `order-service.properties`
- Utilisée pour récupérer les commandes des N derniers jours

### Bases de Données MySQL
- **ecommerce_products** - Product Service (port 8004)
- **ecommerce_orders** - Order Service (port 8005)
- **ecommerce_users** - Client API (port 8006)

### Authentification
- **JWT Secret**: Configuré dans `client-api.properties`
- **Email SMTP**: Gmail configuré pour vérification email

### Ports des Services
- Config Server: 8001
- Eureka Server: 8002
- Gateway: 8003
- Product Service: 8004
- Order Service: 8005
- Client API: 8006
- Frontend: 3000
