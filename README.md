# 🎛️ Blueprints Zigbee2MQTT pour Home Assistant

[![GitHub](https://img.shields.io/github/license/tritrifix/homeassistant-bouton-on-off-z2m)](LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/tritrifix/homeassistant-bouton-on-off-z2m)](https://github.com/tritrifix/homeassistant-bouton-on-off-z2m/stargazers)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-Blueprints-blue)](https://www.home-assistant.io/)
[![Zigbee2MQTT](https://img.shields.io/badge/Zigbee2MQTT-Compatible-green)](https://www.zigbee2mqtt.io/)

Collection de blueprints Home Assistant pour contrôler des appareils via Zigbee2MQTT, avec un focus particulier sur les boutons et télécommandes IKEA STYRBAR.

## 🚀 Import Rapide

Cliquez sur les badges ci-dessous pour importer directement les blueprints dans votre Home Assistant :

| Blueprint | Import |
|-----------|--------|
| **Bouton générique - Actions** | [![Import](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ftritrifix%2Fhomeassistant-bouton-on-off-z2m%2Fblob%2Fmain%2Fzigbee2mqtt_button_actions.yaml) |
| **Bouton universel - Lampe** | [![Import](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ftritrifix%2Fhomeassistant-bouton-on-off-z2m%2Fblob%2Fmain%2Fzigbee2mqtt_button_light.yaml) |
| **STYRBAR - Lampe + Flèches** | [![Import](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ftritrifix%2Fhomeassistant-bouton-on-off-z2m%2Fblob%2Fmain%2Fzigbee2mqtt_ikea_styrbar_4buttons_lights_and_arrows.yaml) |
| **STYRBAR - Actions complètes** | [![Import](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ftritrifix%2Fhomeassistant-bouton-on-off-z2m%2Fblob%2Fmain%2Fzigbee2mqtt_ikea_styrbar_full_actions.yaml) |

## Prérequis

- Home Assistant installé et configuré
- Zigbee2MQTT fonctionnel et publiant des messages MQTT
- Vos appareils Zigbee appairés avec Zigbee2MQTT
- Le JSON publié par Zigbee2MQTT doit contenir une clé `action` (ex: `{"action":"on"}`)

## 📋 Liste des Blueprints

### 1. **zigbee2mqtt_button_actions.yaml**
**Blueprint générique : Actions directes par valeur 'action'**

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ftritrifix%2Fhomeassistant-bouton-on-off-z2m%2Fblob%2Fmain%2Fzigbee2mqtt_button_actions.yaml)

Blueprint flexible permettant de configurer directement dans l'UI Home Assistant quelles actions exécuter selon la valeur de `payload_json.action` reçue via MQTT.

**Caractéristiques :**
- Configuration du topic MQTT du bouton
- Personnalisation des valeurs d'action (on, off, toggle, single, double, hold, etc.)
- Actions de dimming (brightness_move_up, brightness_move_down, brightness_stop)
- Configuration directe des actions à exécuter pour chaque type d'appui

**Cas d'usage :** Idéal quand vous voulez contrôler plusieurs appareils ou exécuter des scénarios complexes avec un bouton.

---

### 2. **zigbee2mqtt_button_light.yaml**
**Blueprint universel : Bouton MQTT → Lampe**

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ftritrifix%2Fhomeassistant-bouton-on-off-z2m%2Fblob%2Fmain%2Fzigbee2mqtt_button_light.yaml)

Blueprint universel optimisé pour contrôler une lampe avec un bouton Zigbee. Inclut une logique de dimming intégrée sans blocage.

**Caractéristiques :**
- Contrôle direct d'une lampe (on/off/toggle)
- Dimming progressif avec boucle limitée dans le temps (évite les blocages)
- Personnalisation des valeurs d'action MQTT
- Support des actions single/double/hold (optionnel)
- Réglage du pas de luminosité et de la vitesse de variation

**Paramètres de dimming :**
- Pas de luminosité (%) par tick (défaut : 7%)
- Intervalle entre chaque tick (défaut : 250ms)
- Durée maximale du dimming (défaut : 3s)

**Cas d'usage :** Parfait pour associer simplement un bouton Zigbee à une lampe avec variation de luminosité.

---

### 3. **zigbee2mqtt_ikea_styrbar_4buttons_lights_and_arrows.yaml**
**IKEA STYRBAR : Contrôle lampe + actions personnalisées sur flèches**

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ftritrifix%2Fhomeassistant-bouton-on-off-z2m%2Fblob%2Fmain%2Fzigbee2mqtt_ikea_styrbar_4buttons_lights_and_arrows.yaml)

Blueprint spécifique pour la télécommande IKEA STYRBAR (E2001/E2002/E2313) offrant un contrôle complet d'une lampe plus des actions personnalisées sur les flèches.

**Caractéristiques :**
- Boutons ON/OFF pour contrôler une lampe
- Dimming intégré et sécurisé (pas de blocage)
- Actions personnalisables pour les flèches gauche/droite :
  - Click (clic simple)
  - Hold (appui long)
  - Release (relâche)

**Actions supportées :**
- `on` / `off`
- `brightness_move_up` / `brightness_move_down` / `brightness_stop`
- `arrow_left_click` / `arrow_left_hold` / `arrow_left_release`
- `arrow_right_click` / `arrow_right_hold` / `arrow_right_release`

**Cas d'usage :** Idéal pour contrôler une lampe principale avec les boutons +/- et utiliser les flèches pour d'autres actions (changer de scène, contrôler des volets, etc.).

---

### 4. **zigbee2mqtt_ikea_styrbar_full_actions.yaml**
[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ftritrifix%2Fhomeassistant-bouton-on-off-z2m%2Fblob%2Fmain%2Fzigbee2mqtt_ikea_styrbar_full_actions.yaml)

**IKEA STYRBAR : Actions personnalisées pour chaque bouton**

Blueprint STYRBAR offrant un contrôle total : toutes les actions sont personnalisables sans logique prédéfinie.

**Caractéristiques :**
- Aucune logique interne de dimming
- Configuration libre de l'action pour chaque bouton
- Vous décidez exactement quoi faire pour chaque événement

**Actions configurables :**
- Bouton ON
- Bouton OFF
- Luminosité + (move up)
- Luminosité - (move down)
- Stop luminosité
- Flèche gauche : click, hold, release
- Flèche droite : click, hold, release

**Cas d'usage :** Maximum de flexibilité pour des automatisations complexes ou quand vous voulez implémenter votre propre logique de dimming via des scripts.

---

## 🚀 Installation

### Méthode recommandée : Import direct

Utilisez les badges d'import dans la section [Import Rapide](#-import-rapide) ci-dessus pour importer directement les blueprints dans Home Assistant en un clic !

### Via l'interface Home Assistant (manuel)

1. Accédez à **Configuration** → **Blueprints**
2. Cliquez sur **Import Blueprint**
3. Collez l'URL du fichier blueprint depuis ce dépôt
4. Cliquez sur **Preview** puis **Import**

### Manuellement (fichiers)

1. Copiez le fichier `.yaml` dans le dossier `config/blueprints/automation/` de votre installation Home Assistant
2. Créez les sous-dossiers si nécessaire
3. Redémarrez Home Assistant ou rechargez les blueprints

---

## 📖 Utilisation

1. Dans Home Assistant, allez dans **Configuration** → **Automatisations & Scènes**
2. Cliquez sur **+ Créer une automatisation**
3. Sélectionnez le blueprint souhaité
4. Configurez :
   - Le topic MQTT de votre bouton (ex: `zigbee2mqtt/button_chambre`)
   - La lampe à contrôler (si applicable)
   - Les actions personnalisées pour chaque bouton
5. Donnez un nom à votre automatisation et sauvegardez

---

## 🔧 Configuration Zigbee2MQTT

Assurez-vous que votre appareil Zigbee2MQTT publie bien un JSON contenant la clé `action`.

**Exemple de message MQTT attendu :**
```json
{
  "action": "on",
  "battery": 100,
  "linkquality": 120
}
```

**Topic MQTT typique :**
```
zigbee2mqtt/nom_de_votre_appareil
```

---

## 💡 Exemples de configuration

### Exemple 1 : Bouton simple pour allumer/éteindre une lampe
Utilisez **zigbee2mqtt_button_light.yaml** :
- Topic MQTT : `zigbee2mqtt/button_salon`
- Lampe : `light.salon`
- Les valeurs par défaut fonctionneront avec la plupart des boutons

### Exemple 2 : STYRBAR pour lampe + scènes sur les flèches
Utilisez **zigbee2mqtt_ikea_styrbar_4buttons_lights_and_arrows.yaml** :
- Topic MQTT : `zigbee2mqtt/styrbar_chambre`
- Lampe : `light.chambre`
- Flèche gauche click : Activer scène "Lecture"
- Flèche droite click : Activer scène "Cinéma"

### Exemple 3 : STYRBAR pour contrôle multi-pièce
Utilisez **zigbee2mqtt_ikea_styrbar_full_actions.yaml** :
- ON : Allumer toutes les lampes du salon
- OFF : Éteindre toutes les lampes du salon
- Flèche gauche : Lancer script dimming personnalisé
- Flèche droite : Contrôler les volets

---

## ❓ FAQ

**Q : Comment trouver le topic MQTT de mon bouton ?**  
R : Dans Zigbee2MQTT, le topic est généralement `zigbee2mqtt/nom_de_l_appareil`. Vous pouvez vérifier dans l'interface Zigbee2MQTT ou avec un client MQTT comme MQTT Explorer.

**Q : Mon bouton ne répond pas**  
R : Vérifiez que :
- Zigbee2MQTT publie bien des messages quand vous appuyez sur le bouton
- Le topic MQTT est correctement configuré dans le blueprint
- Les valeurs d'action correspondent à celles publiées par votre appareil

**Q : Le dimming ne fonctionne pas**  
R : Assurez-vous que votre lampe supporte la variation de luminosité et que Zigbee2MQTT publie bien les actions `brightness_move_up`, `brightness_move_down` et `brightness_stop`.

**Q : Quelle est la différence entre les blueprints STYRBAR ?**  
R : 
- **4buttons_lights_and_arrows** : Contrôle automatique d'une lampe + actions personnalisées sur les flèches
- **full_actions** : Aucune logique prédéfinie, vous configurez tout manuellement

---

## 📝 Licence

Ces blueprints sont fournis "tels quels" pour la communauté Home Assistant. Libre à vous de les utiliser, modifier et partager.

---

## 🤝 Contribution

N'hésitez pas à proposer des améliorations ou à signaler des problèmes !
