# Process Flow

Vista gráfica del proceso de desarrollo con la plantilla **Agentic SDLC basado en SDD**, pensada para presentarla y compartirla. Es un resumen visual: las reglas completas viven en [README.md](README.md#lifecycle), [work-types.md](docs/00-governance/work-types.md) y [quality-gates.md](docs/00-governance/quality-gates.md). Los términos se explican en [GLOSSARY.md](GLOSSARY.md).

## How to Read the Diagrams

| Shape / Color | Meaning |
|---|---|
| Rectángulo azul | Etapa del lifecycle, con su rol responsable y su artefacto principal |
| Hexágono naranja | Quality Gate: punto de control que debe aprobarse para avanzar |
| Rectángulo morado | Aprobación humana ([Human Approval Rules](docs/00-governance/constitution.md#human-approval-rules)) |
| Rombo | Decisión del flujo |
| Línea punteada | Retorno o ciclo de mejora |

Ninguna etapa se omite en silencio: si no aplica a un trabajo, se marca `N/A` con justificación ([Lifecycle Applicability](docs/00-governance/work-types.md#lifecycle-applicability)).

## 1. Big Picture

Del inicio del proyecto al ciclo continuo de trabajo y mejora.

```mermaid
flowchart TD
    START(["Necesidad de software"]) --> Q{"¿El repositorio ya tiene código?"}
    Q -- "No: proyecto nuevo" --> NEW["Use this template en GitHub<br/>+ skill bootstrap-project"]
    Q -- "Sí: proyecto existente" --> ADOPT["Skill adopt-existing-project<br/>sin sobrescribir archivos"]
    NEW --> PROFILE["Proponer Project Profile<br/>LITE · STANDARD · CRITICAL"]
    ADOPT --> PROFILE
    PROFILE --> H1["El humano aprueba el perfil"]
    H1 --> BASE["Base del proyecto, una sola vez<br/>nuevo: Constitution · Discovery · Product Spec<br/>existente: current-state del área afectada"]
    BASE --> LOOP["Ciclo por cada trabajo<br/>clasificar → especificar → planificar →<br/>construir → verificar → revisar → converger"]
    LOOP --> REL["Release y operación<br/>con observabilidad"]
    REL --> LEARN["Learning<br/>incidentes · retrospectivas · tech debt"]
    LEARN --> IMP["Harness Improvement<br/>mejora reglas, skills, gates y sensores"]
    IMP -. "el siguiente trabajo usa el harness mejorado" .-> LOOP
    LOOP -. "siguiente feature, bug o cambio" .-> LOOP

    classDef stage fill:#E8F0FE,stroke:#1A73E8,color:#0B1F44
    classDef human fill:#F3E8FD,stroke:#8E24AA,color:#2E0B3A
    class NEW,ADOPT,PROFILE,BASE,LOOP,REL,LEARN,IMP stage
    class H1 human
```

## 2. Full Lifecycle

Las 20 etapas canónicas con su rol, su artefacto y su gate. La columna 1 se recorre normalmente una vez por proyecto; desde FEATURE SPEC, una vez por cada trabajo, según su Work Type.

```mermaid
flowchart TD
    subgraph P1["1 · Intención y contexto"]
        IDEA["IDEA<br/>Human<br/>problema o solicitud"] --> CLASSIFY["CLASSIFY<br/>Orchestrator<br/>Work Type · ID · applicability"]
        CLASSIFY --> ASSESS["ASSESS<br/>Analyst<br/>current-state · constraints"]
        ASSESS --> G1{{"Assessment Gate"}}
        G1 --> CONST["CONSTITUTION<br/>Human + Orchestrator<br/>reglas obligatorias"]
        CONST --> G2{{"Governance Gate"}}
        G2 --> DISC["DISCOVERY<br/>Analyst<br/>docs/01-discovery"]
        DISC --> G3{{"Discovery Gate"}}
        G3 --> PSPEC["PRODUCT SPEC<br/>Analyst<br/>docs/02-product"]
        PSPEC --> G4{{"Product Gate"}}
    end

    subgraph P2["2 · Especificación y diseño"]
        FSPEC["FEATURE SPEC<br/>Analyst<br/>spec · FR · AC · examples"] --> CLAR["CLARIFY<br/>Analyst + Human<br/>Open Questions"]
        CLAR --> QQ{"¿Quedan preguntas críticas?"}
        QQ -- "Sí" --> CLAR
        QQ -- "No" --> HSPEC["El humano aprueba la spec<br/>Approved by · Date"]
        HSPEC --> G5{{"Spec Gate"}}
        G5 --> ARCH["ARCHITECTURE<br/>Architect<br/>docs/04-architecture · ADR"]
        ARCH --> G6{{"Architecture Gate"}}
        G6 --> CONTR["CONTRACTS<br/>Architect<br/>contracts/ de la spec"]
        CONTR --> G7{{"Contract Gate"}}
    end

    subgraph P3["3 · Planificación"]
        PLAN["IMPLEMENTATION PLAN<br/>Orchestrator + Architect<br/>plan.md · risks.md"] --> G8{{"Plan Gate"}}
        G8 --> DAG["TASK DAG<br/>Orchestrator<br/>tasks.md · dependencies.md"]
        DAG --> G9{{"Implementation Gate"}}
    end

    subgraph P4["4 · Construcción y verificación"]
        EXEC["AGENT EXECUTION<br/>Implementer + Tester<br/>código · tests · progress.md"] --> SENS["FEEDBACK SENSORS<br/>Tester<br/>linter · tests · scanning · evals"]
        SENS --> G10{{"Verification Gate"}}
        G10 -. "falla un sensor bloqueante" .-> EXEC
        G10 --> REV["REVIEW<br/>Reviewer + Security<br/>review.md"]
        REV --> G11{{"Review Gate"}}
        G11 -. "BLOCKER o HIGH abiertos" .-> EXEC
        G11 --> CONV["CONVERGENCE<br/>Orchestrator<br/>traceability.md"]
        CONV --> G12{{"Convergence Gate"}}
        G12 -. "divergencia: definir la intención válida" .-> EXEC
    end

    subgraph P5["5 · Producción y aprendizaje"]
        RELEASE["RELEASE<br/>Human<br/>deployment · rollback"] --> HREL["El humano aprueba el release"]
        HREL --> G13{{"Release Gate"}}
        G13 --> OBS["OBSERVABILITY<br/>Human / Operations<br/>observability · slo · runbook"]
        OBS --> G14{{"Production Ready Gate"}}
        G14 --> LEARN["LEARNING<br/>Orchestrator + Human<br/>docs/08-learning"]
        LEARN --> HI["HARNESS IMPROVEMENT<br/>Human<br/>agents · skills · gates · evals"]
        HI --> HHAR["El humano aprueba el cambio al harness"]
        HHAR --> G15{{"Harness Change Gate"}}
    end

    G4 --> FSPEC
    G7 --> PLAN
    G9 --> EXEC
    G12 --> RELEASE
    G15 -. "siguiente trabajo" .-> CLASSIFY

    classDef stage fill:#E8F0FE,stroke:#1A73E8,color:#0B1F44
    classDef gate fill:#FFF4E5,stroke:#E8710A,color:#3D1F00
    classDef human fill:#F3E8FD,stroke:#8E24AA,color:#2E0B3A
    class IDEA,CLASSIFY,ASSESS,CONST,DISC,PSPEC,FSPEC,CLAR,ARCH,CONTR,PLAN,DAG,EXEC,SENS,REV,CONV,RELEASE,OBS,LEARN,HI stage
    class G1,G2,G3,G4,G5,G6,G7,G8,G9,G10,G11,G12,G13,G14,G15 gate
    class HSPEC,HREL,HHAR human
```

## 3. Work Type Routing

En CLASSIFY, el Orchestrator asigna el Work Type; cada tipo recorre solo las etapas y crea solo los artefactos que necesita ([Artifacts by Work Type](docs/00-governance/work-types.md#artifacts-by-work-type)).

```mermaid
flowchart LR
    C["CLASSIFY<br/>Orchestrator asigna Work Type e ID<br/>y registra el trabajo en docs/05-plans/index.md"] --> T{"¿Qué tipo de trabajo es?"}
    T -- "FEATURE" --> F["Nueva capacidad · spec nueva + plan completo<br/>FEATURE SPEC → CLARIFY → ARCHITECTURE → CONTRACTS →<br/>PLAN → TASK DAG → EXECUTION → SENSORS → REVIEW →<br/>CONVERGENCE → RELEASE"]
    T -- "CHANGE" --> CH["Cambia un comportamiento existente<br/>ASSESS de impacto → actualiza la spec (Change History)<br/>→ resto como FEATURE"]
    T -- "BUG" --> B["Corrige un defecto · plan, tasks, change-record, review<br/>ASSESS → PLAN → FIX → REGRESSION TEST →<br/>SENSORS → REVIEW → CONVERGENCE"]
    T -- "HOTFIX" --> H["Urgencia en producción<br/>Emergency Path (diagrama 5)"]
    T -- "REFACTOR / TECH_DEBT" --> R["Mejora interna · plan, tasks, change-record, review<br/>ASSESS → PLAN → EXECUTION → SENSORS → REVIEW<br/>con evidencia de comportamiento preservado"]
    T -- "SPIKE" --> S["Investigación · plan + findings<br/>ASSESS → EXPERIMENT → FINDINGS → DECISION<br/>su código no pasa a producción"]
    T -- "DOCUMENTATION" --> D["Solo documentos · change-record + review<br/>Cambio → REVIEW"]

    classDef stage fill:#E8F0FE,stroke:#1A73E8,color:#0B1F44
    class C,F,CH,B,H,R,S,D stage
```

## 4. Lifecycle Applicability

Cómo se decide, en CLASSIFY, si una etapa se ejecuta o se marca `N/A` ([Applicability Triggers](docs/00-governance/work-types.md#applicability-triggers)).

```mermaid
flowchart TD
    S["Etapa del trabajo"] --> P["Valor por defecto<br/>según el Project Profile"]
    P --> TR{"¿Hay algún applicability trigger activo?<br/>Security Review · Architecture · Contracts"}
    TR -- "Sí" --> RUN["La etapa se ejecuta"]
    TR -- "No" --> CR{"¿Perfil CRITICAL y etapa<br/>Security Review o Architecture?"}
    CR -- "Sí" --> HUM["N/A solo con aprobación humana"]
    CR -- "No" --> NA{"¿Se propone N/A?"}
    NA -- "No" --> RUN
    NA -- "Sí" --> JUS["N/A en plan.md con triggers<br/>evaluados y justificación"]
    TR -. "se quiere N/A pese al trigger" .-> HUM
    HUM --> JUS
    RUN --> RV["El Reviewer verifica todas<br/>las justificaciones N/A"]
    JUS --> RV
    U["Si no se puede saber si un trigger aplica,<br/>se trata como aplicable"] -.- TR

    classDef stage fill:#E8F0FE,stroke:#1A73E8,color:#0B1F44
    classDef human fill:#F3E8FD,stroke:#8E24AA,color:#2E0B3A
    class S,P,RUN,JUS,RV,U stage
    class HUM human
```

## 5. Emergency Path

Solo para `HOTFIX` ante un incidente crítico; no puede usarse para evitar el proceso normal ([Emergency Change Procedure](docs/00-governance/work-types.md#emergency-change-procedure)).

```mermaid
flowchart LR
    I(["Incidente crítico<br/>en producción"]) --> A["Aprobación humana explícita<br/>en change-record.md"]
    A --> M["Corrección mínima<br/>alcance acotado · rollback definido"]
    M --> V["Verificación crítica<br/>tests críticos disponibles"]
    V --> RL["Release"]
    RL --> O["Observar<br/>métricas y alertas"]
    O --> PI["Completar post-incidente<br/>documentación · spec o change record ·<br/>regression tests · traceability ·<br/>incident report · causa raíz"]
    PI --> FW["Feedback Flywheel<br/>(diagrama 7)"]

    classDef stage fill:#E8F0FE,stroke:#1A73E8,color:#0B1F44
    classDef human fill:#F3E8FD,stroke:#8E24AA,color:#2E0B3A
    class M,V,RL,O,PI,FW stage
    class A human
```

## 6. Task and Spec States

Estados de una tarea en `tasks.md`. El Implementer solo toma tareas `READY`.

```mermaid
stateDiagram-v2
    direction LR
    [*] --> TODO
    TODO --> READY: dependencias en DONE
    READY --> IN_PROGRESS: el Implementer la toma
    IN_PROGRESS --> BLOCKED: impedimento
    BLOCKED --> IN_PROGRESS: impedimento resuelto
    IN_PROGRESS --> REVIEW: sensores en verde y evidencia
    REVIEW --> IN_PROGRESS: cambios solicitados
    REVIEW --> DONE: verificada y revisada
    DONE --> [*]
```

Estados de una spec en `spec.md`. Solo un humano la pasa a `Approved`.

```mermaid
stateDiagram-v2
    direction LR
    [*] --> Draft
    Draft --> Clarification: hay Open Questions
    Draft --> Approved: aprobación humana
    Clarification --> Approved: sin preguntas críticas y aprobación humana
    Approved --> Implementing: inicia la construcción
    Implementing --> Validating: verificación y revisión
    Validating --> Done: Convergence Gate aprobado
    Done --> Deprecated: reemplazada o retirada
```

## 7. Feedback Flywheel

Cada incidente o fallo repetido mejora el sistema que produce software, no solo el código ([Feedback Flywheel](docs/08-learning/README.md)).

```mermaid
flowchart LR
    SIG["Señal<br/>incidente · bug · fallo repetido · retrospectiva"] --> AN["Analizar<br/>causa raíz + harness gap"]
    AN --> IM["Mejorar el harness<br/>spec · tests · evals · gates ·<br/>skills · agentes · docs · sensores"]
    IM --> HC{{"Harness Change Gate<br/>si el cambio es relevante"}}
    HC --> VE["Verificar<br/>sensor, test o eval que<br/>detectaría la recurrencia"]
    VE --> RE["Registrar<br/>lessons-learned.md"]
    RE -. "el sistema aprende" .-> SIG

    classDef stage fill:#E8F0FE,stroke:#1A73E8,color:#0B1F44
    classDef gate fill:#FFF4E5,stroke:#E8710A,color:#3D1F00
    class SIG,AN,IM,VE,RE stage
    class HC gate
```

## 8. Roles at a Glance

| Role | Stages | Main Artifacts |
|---|---|---|
| Human | IDEA, CONSTITUTION, RELEASE, OBSERVABILITY, HARNESS IMPROVEMENT y todas las aprobaciones | Decisiones registradas en el repositorio |
| [Orchestrator](agents/orchestrator.md) | CLASSIFY, IMPLEMENTATION PLAN, TASK DAG, CONVERGENCE, LEARNING | `docs/05-plans/index.md`, `plan.md`, `tasks.md`, `progress.md` |
| [Analyst](agents/analyst.md) | ASSESS, DISCOVERY, PRODUCT SPEC, FEATURE SPEC, CLARIFY | `docs/01-discovery/`, `docs/02-product/`, spec |
| [Architect](agents/architect.md) | ARCHITECTURE, CONTRACTS, IMPLEMENTATION PLAN | `docs/04-architecture/`, ADR, `contracts/` |
| [Implementer](agents/implementer.md) | AGENT EXECUTION | Código y tests |
| [Tester](agents/tester.md) | AGENT EXECUTION, FEEDBACK SENSORS | Tests, evals, `traceability.md` |
| [Reviewer](agents/reviewer.md) | REVIEW | `review.md` |
| [Security](agents/security.md) | REVIEW, cuando aplica Security Review | Hallazgos de seguridad en `review.md` |
