## 🧱 FASE 1: BOT CURATORIAL (Scraping ligero)

### 🎯 Objetivo

Construir un pequeño sistema que te sugiera pares interesantes basados en **tu propio criterio estético**, no en el hype genérico. Así, empiezas a formar una **colección coherente**, no solo reactiva.

---

## 🧠 ENFOQUE CURATORIAL: ¿Cómo definimos “par interesante”?

Para entrenar al bot a sugerir bien, primero necesitamos definir tu criterio.  
Te propongo que lo filtremos en tres niveles:

### 1. **Filtros básicos (scraping)**

- Precio máximo
    
- Talla(s) objetivo
    
- Estado (nuevo / usado)
    
- Ubicación geográfica (si es relevante)
    

### 2. **Filtros semánticos (descripciones / título)**

- ¿Qué palabras clave reflejan tu gusto? Ej: “minimal”, “beige”, “retro”, “avant-garde”, “experimental”, “Yeezy”, “Jordan 1”, etc.
    

### 3. **Filtros visuales (opcional, más adelante)**

- Dominancia de ciertos colores o formas.
    
- Clasificación automática por estilo usando IA de visión.
    

---

## 🛠️ TECNOLOGÍA BASE SUGERIDA

- **Lenguaje**: Python (flexible y muy usado en scraping)
    
- **Herramientas**:
    
    - `requests` + `BeautifulSoup` o `Selenium` (para scraping web)
        
    - API de plataformas si está disponible (ej. GOAT, StockX)
        
    - Base de datos mínima con SQLite o Airtable
        
    - Notificaciones: email o Telegram Bot
        

---

## 🧪 POSIBLES FUENTES PARA SCRAPEAR

| Plataforma         | Notas                                                                |
| ------------------ | -------------------------------------------------------------------- |
| **Wallapop**       | Buen sitio para cazar rarezas y chollos locales. Ideal para empezar. |
| **Vinted**         | Similar a Wallapop, pero más enfocado en moda.                       |
| **Zalando Lounge** | Restocks y ofertas flash. Algunas joyas ocultas.                     |
| **StockX / GOAT**  | Precio alto pero buenos datos para valorar rareza y tendencia.       |