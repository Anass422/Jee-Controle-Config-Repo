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
- Frontend: 8080

## 🚀 Utilisation

Ce repository est utilisé par le **Spring Cloud Config Server** pour centraliser toutes les configurations.

### Configuration du Config Server

```properties
spring.cloud.config.server.git.uri=https://github.com/Anass422/Jee-Controle-Config-Repo.git
spring.cloud.config.server.git.default-label=main
```

### Accès aux Configurations

Les services récupèrent leurs configurations via :
```
http://localhost:8001/{service-name}/default
```

Exemples :
- `http://localhost:8001/product-service/default`
- `http://localhost:8001/order-service/default`
- `http://localhost:8001/client-api/default`

## 🔄 Rafraîchissement Dynamique

Pour rafraîchir la configuration d'un service sans redémarrage :

```bash
curl -X POST http://localhost:{port}/actuator/refresh
```

Exemple pour Order Service :
```bash
curl -X POST http://localhost:8005/actuator/refresh
```

## 📝 Modification des Configurations

1. Modifier le fichier `.properties` souhaité
2. Commit et push vers GitHub
3. Appeler l'endpoint `/actuator/refresh` du service concerné

## 🔐 Sécurité

⚠️ **Important** : Les mots de passe et secrets sont en clair dans ce repository de démonstration. 

Pour la production :
- Utiliser Spring Cloud Config avec encryption
- Utiliser des variables d'environnement
- Utiliser un vault (HashiCorp Vault, AWS Secrets Manager, etc.)

## 📧 Configuration Email

L'envoi d'emails utilise Gmail SMTP :
- Host: smtp.gmail.com
- Port: 587
- Credentials configurés dans `client-api.properties`

---

**Projet E-Commerce Microservices**
Développé avec Spring Boot 3.5.8 & Java 21
