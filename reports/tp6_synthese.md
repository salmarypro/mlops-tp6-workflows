# Orchestrateur ou integration continue ? (TP06)

| Critere                           | Prefect (orchestrateur)                      | GitHub Actions (CI)                          |
|-----------------------------------|----------------------------------------------|----------------------------------------------|
| Ce qui declenche l'execution      | Un horaire (cron lundi 6 h) ou un Quick run  | Un git push ou le bouton Run workflow        |
| Ou s'execute le traitement        | Sur notre poste (serve ou worker)            | Sur une machine Linux GitHub (ubuntu-latest) |
| Qui surveille, et ou              | L'equipe, dans l'interface Prefect (Runs)    | Le developpeur, dans l'onglet Actions        |
| Ce qui se passe en cas d'echec    | Run Failed, taches suivantes non executees   | Etape rouge, commit marque en rouge          |
| Type de tache adapte              | Traitements recurrents (reentrainement)      | Verification du code a chaque modification   |
| Ce qui est versionne dans Git     | flow_mlops.py, planifier.py, prefect.yaml    | .github/workflows/ci.yml, verifier_qualite.py|

## Conclusion 
La chaine d'integration continue valide le code a chaque modification.
L'orchestrateur execute et surveille des traitements recurrents.
Prefect a arrete le workflow sur la regle de qualite (F1 0.25 < 0.82), GitHub Actions a bloque le commit degrade.
Les deux appliquent la meme regle de qualite, mais a des moments differents.
Ils sont complementaires : aucun ne remplace l'autre.