# Learn Kafka with Python

A lightweight Apache Kafka project demonstrating a message producer and consumer using Python and [`confluent-kafka`](https://github.com/confluentinc/confluent-kafka-python).

---

## 📁 Project Structure

```text
.
├── docker-compose.yml   # Local Apache Kafka broker (KRaft mode)
├── producer.py         # Kafka producer sending order events
├── tracker.py          # Kafka consumer tracking and reading order events
├── requirements.txt    # Python dependencies
├── .gitignore          # Git ignore rules for Python & IDE files
└── README.md           # Project documentation
```

---

## 🚀 Getting Started

### 1. Prerequisites

- **Python 3.9+**
- **Docker & Docker Compose** (for running local Kafka broker)

---

### 2. Start the Kafka Broker

Start Apache Kafka in KRaft mode (no Zookeeper required):

```bash
docker compose up -d
```

Verify that the Kafka container is up and healthy:

```bash
docker compose ps
```

---

### 3. Setup Python Virtual Environment

Create and activate a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

---

### 4. Run the Project

#### Step A: Start the Consumer (Order Tracker)

In terminal window 1:

```bash
python tracker.py
```

Output:
```text
Consumer is running and subscribed to orders topic
```

#### Step B: Start the Producer (Send Orders)

In terminal window 2:

```bash
python producer.py
```

Output:
```text
Delivered: {"order_id": "...", "user": "Gehrman Sparrow", "item": "creeping hunger", "quantity": 2, "price": 99.99}
Delivered to topic: orders | partition: 0 | offset: 0
```

The consumer will immediately receive and display the message:
```text
Received order: 2 x creeping hunger ($99.99) from Gehrman Sparrow
```

---

### 5. Stopping Kafka

When you're done, stop the Kafka broker:

```bash
docker compose down
```
