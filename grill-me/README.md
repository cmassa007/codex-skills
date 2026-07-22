# grill-me

Skill de Codex para realizar una entrevista rigurosa de descubrimiento antes de implementar un proyecto.

## Contenido

- `SKILL.md`: reglas, proceso de entrevista, criterios de preparación y entregable final.
- `agents/openai.yaml`: nombre visible, descripción breve, prompt sugerido e invocación implícita.

## Instalación

### Opción global

Copia la carpeta `grill-me` dentro de:

```text
$HOME/.agents/skills/
```

Quedará así:

```text
$HOME/.agents/skills/grill-me/SKILL.md
```

### Opción por repositorio

Copia la carpeta dentro del repositorio:

```text
<REPO>/.agents/skills/grill-me/
```

## Uso

Invocación explícita:

```text
$grill-me Quiero crear una plataforma para gestionar solicitudes de clientes.
```

También puede activarse implícitamente cuando Codex detecte que se está iniciando un proyecto con requisitos incompletos.

## Comportamiento esperado

La skill hará una sola pregunta por turno, no escribirá código durante la entrevista y no permitirá implementar hasta que presentes una aprobación explícita del plan.
