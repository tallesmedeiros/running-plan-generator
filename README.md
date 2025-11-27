# Running Plan Generator (VDOT / Daniels-like)

Projeto em Python para gerar planos de treino de corrida de forma determinística,
usando VDOT estimado a partir de desempenho em prova (formulação ao estilo Daniels).

## Instalação

```bash
pip install -r requirements.txt
```

## Uso rápido

```python
from running_plan_generator import (
    AthleteConfig, Objective, generate_plan, plan_to_dataframe,
    sanity_check_zone_distribution,
)

config = AthleteConfig(
    name="Atleta Teste",
    objective=Objective.TEN_K,
    initial_weekly_volume_km=40.0,
    frequency_per_week=5,
    max_weekly_volume_km=70.0,
    race_distance_km=10.0,
    race_time_min=40.0,
    has_injury_history=False,
)

plan = generate_plan(config, num_weeks=16, feedback_list=None)
df_plan = plan_to_dataframe(plan)
df_sanity = sanity_check_zone_distribution(plan)
print(df_plan.head())
print(df_sanity.head())
```

Depois é só exportar o DataFrame para Excel, CSV, etc.

## Estrutura

- `src/running_plan_generator/` — código principal do gerador.
- `examples/` — exemplos de uso.
- `tests/` — (esqueleto) para futuros testes unitários.
# RunningPlan
