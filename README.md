# Git skill

Convenciones Git y generación de mensajes de commit siguiendo Conventional Commits v1.0.0. Incluye reglas para tipos, scope, descripción, cuerpo, breaking changes y footers. Los mensajes proporcionados explícitamente por el usuario se conservan sin modificar.

Repositorio: https://github.com/Entaina/git-skill

## Instalación

Instalación en el proyecto actual:

```bash
npx skills add Entaina/git-skill --skill git
```

Para instalar en el ámbito de usuario, añade `-g`. El CLI permite seleccionar los agentes destinatarios; la disponibilidad de comandos como `/git:commit` depende del agente y de su configuración, y esta skill no crea ese comando.

## Estructura

- `skills/git/SKILL.md`: instrucciones y metadatos de la skill instalable.
- `skills/git/references/conventional-commits-v1.0.0.md`: referencia de Conventional Commits.
- `AGENTS.md`: instrucciones para contribuir.
- `.github/workflows/release-please.yml`: automatización de versiones.
- `release-please-config.json` y `.release-please-manifest.json`: configuración de Release Please.

## Desarrollo y versiones

Esta copia es la fuente de distribución. La extracción no modifica la skill original instalada ni configura sincronización automática con ella.

Usa Conventional Commits al contribuir. Release Please propone una primera versión `0.1.0`; el tag y la GitHub Release se crean al fusionar la PR de release, no con el primer push. La estrategia `simple` mantiene `version.txt` y `CHANGELOG.md` en la raíz mediante las PR de release.

El workflow utiliza el `GITHUB_TOKEN` predeterminado, sin secretos adicionales. GitHub Actions debe estar habilitado y autorizado a crear pull requests. Las PR y releases creadas con ese token no activan otros workflows automáticamente.

La instalación mediante skills.sh y el ciclo de releases se verifican por separado; el comando anterior no selecciona ni fija una GitHub Release concreta.

La referencia incluida identifica su fuente oficial: https://www.conventionalcommits.org/en/v1.0.0/.
