# Log-680-Equipe-7

# Laboratoire 1

## Wiki
Bienvenue dans le Wiki de notre projet. Vous y découvrirez une documentation complète et détaillée sur les divers aspects de notre travail.

### Sections du wiki
- [Création d’un projet et du tableau Kanban dans GitHub](wiki/creating_project_kanban_board.md)
- [Création des étiquettes et jalons ](wiki/creating_labels_milestones.md)
- [Ajout de modèles](wiki/templates.md)
  - [Modèle de tâche: Développement](wiki/task_development_template.md)
  - [Modèle de tâche: Planification](wiki/task_planning_template.md)
  - [Modèle pour les «Pull Requets»](wiki/pull_request_template.md)
- [Politique de branches ](wiki/branch_policy.md)
- [Création de l'application](wiki/creating_application.md)
- [Métriques Kanban ](wiki/kanban_metrics.md)
- [Métrique “Pull Request” ](wiki/pull_request_metrics.md)
- [Base de données](wiki/database.md)
- [Tests](wiki/tests.md)

## First Time Setup

**Step 1 - Create virtual environment**
- `python -m venv env`

**Step 2 - Go to virtual env directory**
- On windows: `env\Scripts\activate`
- On Mac: `source env/bin/activate`

**Step 3 - Install all dependencies**
- On windows: `pip install fastapi sqlalchemy psycopg2 requests pytest pydantic uvicorn`  
- On Mac: `pip install fastapi sqlalchemy psycopg2-binary requests pytest pydantic uvicorn`  

**Step 4 - Create DB tables (only one person per team needs to do this)**
- `python initialize_db.py`

**Step 5 - Run the API**
- `python run.py`

**Step 6 - Deactivate virtual environment**
- `deactivate`

## Explication des routes

### Routes pour les métriques Kanban

**Métrique 1: Temps (lead time) pour une tâche donnée**  
**Route:** *`GET /kanban/lead-time-task`*

**Métrique 2: Temps (lead time) pour les tâches terminées dans une période donnée**  
**Route:** *`GET /kanban/lead-time-period`*

**Métrique 3: Nombre de tâches actives pour une colonne donnée**  
**Route:** *`GET /kanban/active-tasks`*

**Métrique 4: Nombre de tâches complétées pour une période donnée**  
**Route:** *`GET /kanban/completed-tasks`*

### Routes pour les métriques Pull-Requests  

**Métrique PR1: Temps pour fusionner (Time to Merge)**  
**Route:** *`GET /pull-requests/time-to-merge`*

**Métrique PR2: Nombre de commentaires (Number of Comments)**  
**Route:** *`GET /pull-requests/number-of-comments`*

**Métrique PR3: Nombre de révisions (Number of Reviews)**  
**Route:** *`GET /pull-requests/number-of-reviews`*

**Métrique PR4: Temps d'approbation (Approval Time)**  
**Route:** *`GET /pull-requests/approval-time`*

**Métrique PR5: Nombre de modifications demandées (Number of Changes Requested)**  
**Route:** *`GET /pull-requests/changes-requested`*

## Troubleshooting

If you get the following error on Windows at step 2: 
"Cannot be loaded because running script is disabled...".

- On VS Code, `CTRL + SHIFT + P` and type "settings.json".
- Add the following in the settings.json file (VS Code restart required): 
`"terminal.integrated.profiles.windows": {
  "PowerShell": {
    "source": "PowerShell",
    "icon": "terminal-powershell",
    "args": ["-ExecutionPolicy", "Bypass"]
  }
},
"terminal.integrated.defaultProfile.windows": "PowerShell",`
