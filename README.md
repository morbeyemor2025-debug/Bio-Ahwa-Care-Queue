# Bio Ahwa Care Queue

Base de code Next.js prête à pousser sur GitHub avant déploiement Vercel.

SaaS médical WhatsApp-first pour cliniques, laboratoires et cabinets médicaux africains francophones: file d'attente, rendez-vous, récupération de résultats, suivi patient et multi-clinique.

## Stack

- Next.js 15 App Router
- TypeScript
- Tailwind CSS
- shadcn/ui-style components locaux
- Supabase Auth, PostgreSQL, RLS et Realtime
- Server Actions
- PWA installable
- Vercel

## Installation locale

```bash
npm install
npm run dev
```

Ouvre ensuite `http://localhost:3000`.

## Pages incluses

- `/` : présentation produit
- `/dashboard/bio-ahwa-du-rail` : dashboard secrétariat
- `/join/bio-ahwa-du-rail` : ajout patient avec ou sans téléphone
- `/doctor/bio-ahwa-du-rail` : interface médecin
- `/analytics/bio-ahwa-du-rail` : statistiques
- `/results/BAH-2026-L022` : suivi public résultats

## Fonctionnalités couvertes

- Ajout patient manuel sans compte, email ou téléphone
- Mode patient WhatsApp avec lien `wa.me`
- Mode patient sans téléphone avec ticket imprimable et QR interne
- Statuts de file: `waiting`, `called`, `in_consultation`, `lab_processing`, `results_ready`, `completed`, `absent`, `cancelled`
- Architecture multi-clinique
- Schéma Supabase complet: `clinics`, `users`, `patients`, `appointments`, `queues`, `queue_entries`, `doctors`, `lab_results`, `notifications`, `audit_logs`
- RLS Supabase et fonctions utilitaires
- Realtime activé pour file, rendez-vous et résultats
- PWA avec manifest et service worker léger

## Variables d'environnement

Copie `.env.example` vers `.env.local`, puis remplis les valeurs:

```bash
cp .env.example .env.local
```

## Déploiement Vercel

1. Crée un repo GitHub.
2. Pousse ce dossier sur GitHub.
3. Importe le repo dans Vercel.
4. Ajoute les variables d'environnement dans Vercel.
5. Lance le premier déploiement.

## Commandes utiles

```bash
npm run lint
npm run build
```

## Supabase

1. Crée un projet Supabase.
2. Ouvre SQL Editor.
3. Exécute `supabase/schema.sql`.
4. Exécute `supabase/seed.sql`.
5. Active Auth email/password selon le besoin.
6. Copie `NEXT_PUBLIC_SUPABASE_URL` et `NEXT_PUBLIC_SUPABASE_ANON_KEY`.
7. Ajoute les variables dans `.env.local` et dans Vercel.

## Commandes GitHub

```bash
git init
git add .
git commit -m "Initial Bio Ahwa Care Queue SaaS"
git branch -M main
git remote add origin https://github.com/morbeyemor2025-debug/bio-ahwa-care-queue.git
git push -u origin main
```

## Prochain branchement métier

Les écrans sont prêts avec données démo. Les prochains branchements naturels sont:

- remplacer `lib/demo-data.ts` par des requêtes Supabase;
- connecter `app/actions/patients.ts` au formulaire;
- ajouter un composant client Realtime abonné à `queue_entries`;
- générer les QR codes serveur à partir de `qr_token` et `tracking_id`;
- ajouter les écrans login Supabase Auth par rôle.
