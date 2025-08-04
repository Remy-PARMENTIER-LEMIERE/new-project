# Débuter sur Nextjs 

Voici un projet Nextjs fraîchement initialisé avec Biome. Cette configuration bien que basique me semble idéale pour commencer à s'entrainer sur cet outil. 

🛠️ Ce projet sera évolutif au fil de ma découverte de l'outil ! D'autres branches viendront surement avec une configuration plus avancée du projet !

## Pour commencer 2 options : 

  ### 1. Fork :
    
  - Fork ce GitRepository pour en créer une copie dans vos propres Repository GitHub.
  - <code>git clone</code> depuis <strong>VOTRE</strong> repository pour récupérer le projet le projet sur votre machine.
  - Sans oublier <code>npm i</code> bien évidemment.

  ### 2. Initialiser vous même le projet :

  - Créez un repository <strong>vide</strong> sur GitHub
  - <code>npx create-next-app@latest &lt;nom-du-projet&gt;</code> Initialise le projet Nextjs (❗Le nom du projet doit être en minuscules)
  <img width="716" height="131" alt="image" src="https://github.com/user-attachments/assets/a60d6815-10c5-4fd8-ad01-100381c1a211" />
  
  - <code>cd &lt;nom-du-projet&gt;</code>
  - <code>npx @biomejs/biome init</code>
  - <code>npx biome migrate eslint</code>
  - <code>npx biome migrate prettier</code>
  - <code>npm install --save-dev --save-exact @biomejs/biome</code>
  - <code>git remote add origin &lt;clef-SSH-du-repo-initialisé-au-début&gt;</code>
  - Quelques petits ajustements dans 2 fichiers :

  #### next.config.ts
  ```ts
  import type { NextConfig } from "next";

  const nextConfig: NextConfig = {
	eslint: {
		ignoreDuringBuilds: true,
	},
  };

  export default nextConfig;
  ```

  #### package.json
  ```json
  "scripts": {
    "biome:check": "biome check --apply --organize-imports .",
    "biome:format": "biome format --write .",
    "dev": "next dev --turbopack",
    "build": "next build",
    "start": "next start"
  },
  ```

  #### Installer Prisma avec MySQL

  - <code>npm i prisma --save-dev</code>
  - <code>npx prisma init --datasource-provider mysql</code> 
  - Paramêtrer grâce au .env.sample le .env qui vient de se créer. 
  - <code>npx prisma db push</code> pour initialiser la base de données
  - Dans <code>src/app</code> créer un dossier <code>lib</code> et à l'intérieur un fichier <code>prima.ts</code> puis copier le code suivant à l'intérieur :

  ```ts
  // lib/prisma.ts
  import { PrismaClient } from "@/generated/prisma";

  const globalForPrisma = global as unknown as { prisma: PrismaClient };

  export const prisma = globalForPrisma.prisma || new PrismaClient();

  if (process.env.NODE_ENV !== "production") globalForPrisma.prisma = prisma;
  ```


## Et Zé Bartiiii !!! 🚀

Vous voici prêts pour débuter votre nouvel apprentissage de cette techno !!

NB: La suite de ce Readme est celui créé à l'initialisation d'un projet Nextjs

  

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
