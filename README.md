# Paupière pour macOS

Paupière tient le Mac éveillé autrement que `caffeinate` : cinq modes en un clic dans la barre des menus, une fin
toujours prévue, des garde-fous, et un MacBook en 3D qui montre ce qui va se passer avant qu'on lance.
Aucun compte, aucune télémétrie.

- **Éveillé** : l'écran reste allumé, rien ne dort.
- **Écran éteint** : l'écran s'éteint tout de suite, les tâches continuent.
- **Verrouillé actif** : la session se verrouille pour de vrai, les tâches continuent derrière le mot de passe.
- **Faux écran** : un voile (noir, horloge, image, message) sur chaque écran. Ce n'est pas un verrou : au premier geste,
  Paupière verrouille la vraie session.
- **Voile protégé** : un voile en mode kiosque, levé par Touch ID ou un code propre à Paupière ; la session reste ouverte
  (le VPN ne tombe pas). Plus faible qu'un verrou de macOS.
- **Capot fermé** : sur secteur, sans écran externe, le Mac reste éveillé capot fermé (aide root, remise à zéro à la fin).

Un MacBook en 3D montre ce qui va se passer ; des situations en grandes cartes ; un raccourci clavier par mode.
Fins automatiques : minuterie, heure, programme terminé, processeur ou réseau calmes. Après : vraie veille ou retour
normal. Garde-fous : 4 h au plus, batterie 20 %, chaleur, économie d'énergie, « toujours là ? » au bout d'une heure.
Aucun faux signal de présence : Teams et Slack vous voient absent pendant une session.

Ce dépôt ne contient que les versions à installer. Le code source n'est pas public.

## Ce qu'il faut

- un Mac à puce Apple (M1 ou plus récent) ;
- macOS 14 ou plus.

## Installer

Dans Terminal (Cmd + Espace, « Terminal »), une seule commande, qui installe aussi les mises à jour :

```
curl -fsSL https://raw.githubusercontent.com/LucasHRCHatReply/paupiere-releases/main/installer.sh | zsh
```

Pour le mode « Capot fermé », installer dans /Applications (mot de passe administrateur demandé une fois) :

```
curl -fsSL https://raw.githubusercontent.com/LucasHRCHatReply/paupiere-releases/main/installer.sh | zsh -s -- --systeme
```

Le script télécharge la dernière version, vérifie l'empreinte SHA-256 du zip, l'identifiant de l'app et sa signature
(équipe Apple `JT9FY7PP7K`, `codesign --verify --deep --strict`), copie l'app, puis l'ouvre. Il garde les réglages.

Autre voie : télécharger `Paupiere.dmg` dans les [Releases](../../releases/latest), l'ouvrir, glisser Paupière sur
Applications. Le disque est signé, non notarisé : au premier lancement, clic droit sur l'app › Ouvrir.
