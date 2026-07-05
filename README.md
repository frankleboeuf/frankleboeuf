# 🐄 FrankLeBoeuf Clicker

Un jeu de type **clicker / idle** sur **Frank Leboeuf**.

## 🎮 Concept

Avant de vendre votre voiture vous devez d'abord rouler avec. Roulez, roulez avec FrankLeBoeuf, achetez des upgrades qui vous font accélérer et découvrez les **easter eggs** sur FrankLeBoeuf.

### Les Upgrades (générateurs) envisagés

- 🐂 Troupeaux de Bœufs
- ⚽ Ballon de Foot
- 👟 Chaussures Skechers
- 📺 Pub `vendezvotrevoiture.fr` qui défile
- ⛄ Bonhomme vert de Cetelem
- 💰 Bouton « Vendre sa voiture »
- 💸 Pluie de thune
- 🥅 But de Frank Leboeuf
- 📧 Emails de Frank Leboeuf
- 📀 DVD Bluray Frank Leboeuf Cars
- 🎥 Absolute FrankLeBoeuf
- 📈 Investissez sur FrankLeBoeuf
- 💪 L'incroyable FrankLeBoeuf
- 🚗 Concessionnaire Carglass _(fin)_

## 🧱 Stack

- **[Next.js 16](https://nextjs.org)** (App Router) + **React 19**
- **TypeScript** (strict)
- **Tailwind CSS 4**
- **[Zustand](https://github.com/pmndrs/zustand)** — state management léger (game loop + store)
- **pnpm** comme gestionnaire de paquets

## 💾 Données & sauvegarde

- **Config des upgrades** : décrite en **JSON** (`data/upgrades.json`), typée via `UpgradeDef` (`lib/types.ts`). La donnée n'existe qu'à **un seul endroit** (le JSON) ; le type ne fait que décrire sa forme, il ne la duplique pas.
- **Events** : en **TypeScript** (ils portent des effets/animations non sérialisables en JSON).
- **Progression du joueur** : **aucune sauvegarde** pour l'instant, tout vit en mémoire (reset au refresh). Si le besoin arrive plus tard :
  - save locale, 1 joueur → **`localStorage`** (via le middleware `persist` de Zustand) ;
  - classement / cross-device → **vraie base de données** (jamais un fichier JSON réécrit côté serveur : pas de transactions, ça se corrompt dès qu'il y a de la concurrence).

En résumé, le JSON est ici un **format de contenu** (config statique), pas un moteur de base de données.

## Lancer le serveur en dev

```bash
pnpm install
pnpm dev
```

Ouvrir [http://localhost:3000](http://localhost:3000).

## 📜 Scripts

| Commande     | Description                         |
| ------------ | ----------------------------------- |
| `pnpm dev`   | Serveur de développement            |
| `pnpm build` | Build de production                 |
| `pnpm start` | Build de production (port **3001**) |
| `pnpm lint`  | Linter (ESLint)                     |
