# Paupière pour macOS

Paupière tient le Mac éveillé autrement que `caffeinate` : des modes en un clic dans la barre des menus, une fin
toujours prévue, des garde-fous, et un MacBook en 3D qui montre ce qui va se passer avant qu'on lance.
Aucun compte, aucune télémétrie.

- **Capot ouvert** : le Mac ne dort pas tant que le capot est ouvert ; le fermer l'endort comme d'habitude.
- **Capot fermé + écran** : le mode natif d'Apple, capot fermé sur un écran externe et le secteur.
- **Jamais en veille** : sur secteur, le Mac ne dort pas même capot fermé sans écran (aide système, remise à zéro à la fin
  et si l'app plante ; ne tient que câble branché).
- **Pause café** : un voile sur chaque écran, levé par Touch ID ou un code propre à Paupière ; la session reste ouverte
  (le VPN ne tombe pas). Un voile, pas un verrou.
- **Autres modes** : Écran éteint, Verrouillé actif, Faux écran (au premier geste, la vraie session se verrouille).
- **Qui veille** : ce qui empêche le Mac de dormir (programmes, micro, caméra), et le bilan de la dernière absence.

Fins automatiques : minuterie, heure, programme terminé, processeur ou réseau calmes. Après : vraie veille ou retour
normal. Garde-fous réglables : 4 h au plus, batterie 20 %, chaleur, économie d'énergie, « toujours là ? » au bout d'une
heure. Aucun faux signal de présence : Teams et Slack vous voient absent pendant une session.

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
Applications. Le disque est signé, non notarisé : au premier lancement, macOS 15 ou plus demande Réglages Système › Confidentialité et sécurité › « Ouvrir quand même » ; macOS 14 : clic droit sur l'app › Ouvrir.
