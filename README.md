# 📡 MeshAlert Sénégal

> Application mobile communautaire basée sur un réseau maillé (Mesh Network) pour la communication d'urgence **sans connexion Internet**.

## 🌍 Objectif

**MeshAlert Sénégal** vise à connecter les citoyens dans les zones non couvertes par le réseau mobile ou lors de coupures Internet, afin de permettre :
- La **messagerie locale** via Bluetooth / WiFi Direct
- L'envoi d'alertes **SOS** géolocalisées
- La **sécurité communautaire**, même hors ligne

## ✨ Fonctionnalités principales

- 📶 Réseau maillé décentralisé (Bluetooth/WiFi P2P)
- 💬 Chat texte hors-ligne
- 🚨 Bouton d'alerte SOS avec géolocalisation
- 🔒 Données chiffrées de bout en bout (E2EE)
- 🔗 Re-transmission automatique des messages (TTL)
- 📡 Autonomie même en cas de panne réseau

## 📱 Technologies utilisées

- **Frontend** : Flutter (Dart)
- **Backend local** : P2P mesh logic (Bluetooth / WiFi Direct)
- **Chiffrement** : AES / RSA
- **Carte** : MapLibre / OpenStreetMap
- **Stockage local** : SQLite

## 🧠 Architecture du message

```json
{
  "id": "bf23a2d1-...",
  "type": "chat" | "SOS",
  "sender": "device_id",
  "timestamp": 1623456789,
  "ttl": 3,
  "body": "Hello world !" | { "coords": [48.85, 2.35] },
  "encrypted": true
}
```

### 🔁 Pseudo-code de propagation

```js
onMessageReceived(msg) {
  if (msg.id in receivedMessages) return;
  receivedMessages.add(msg.id);
  if (msg.ttl > 0) {
    msg.ttl -= 1;
    for (neighbor in neighbors) {
      sendMessage(neighbor, msg);
    }
  }
}
```

## 🧭 Cas d’usage concrets

- Zones rurales sans réseau mobile
- Manifestations ou coupures d’Internet
- Urgences en zones non couvertes
- Réseaux de quartier pour la sécurité citoyenne

## 📌 Roadmap

| Version | Fonctionnalités prévues |
|---------|--------------------------|
| 0.1.0 (Alpha) | Chat local, détection Bluetooth, bouton SOS |
| 0.2.0 (Beta)  | Relais Mesh, carte des alertes |
| 1.0.0         | Support multi-villes, collaboration ONG |

## 🛠️ Installation pour développeurs

```bash
git clone https://github.com/votre-utilisateur/meshalert-senegal.git
cd meshalert-senegal
flutter pub get
flutter run
```

## 🧑‍🤝‍🧑 Contribuer

Les contributions sont les bienvenues ! Pour proposer une fonctionnalité, ouvrez une *issue* ou un *pull request*.

## 📄 Licence

Ce projet est sous licence **MIT**. Voir le fichier [LICENSE](LICENSE).

## 🔗 Liens utiles

- Maquette Figma (à venir)
- Documentation technique (en cours)
- Tutoriel vidéo d’installation (prévu)