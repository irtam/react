# Photocatalytic Reactor Simulation Framework

Questo repository contiene una pipeline modulare per la simulazione numerica di reattori fotocatalitici, divisa in vari team operativi, coordinati tramite orchestratore e interfacce standard in YAML.

---

## Struttura del Progetto

```
photoreactor/
├── input/                      # File YAML forniti dal Team Modello
│   ├── reaction_model.yaml
│   ├── geometry.yaml
│   ├── catalyst.yaml
│   ├── optical_properties.yaml
│   └── environment.yaml
├── output/                     # Risultati generati da ogni modulo
│   ├── kinetic_output.yaml
│   ├── light_field.yaml
│   ├── flow_field.yaml
│   └── reactor_simulation.yaml
├── orchestrator/              # Motore centrale che coordina tutti i passi
│   ├── orchestrator.yaml
│   └── run_orchestration.py
├── modules/                   # Codice per i singoli moduli numerici
│   ├── kinetics_solver.py
│   ├── dom_solver.py
│   ├── flow_solver.py
│   └── coupler.py
├── scripts/                   # Validazione, conversioni, pre/post-processing
│   ├── validate_inputs.py
│   └── generate_mesh_from_geometry.py
└── README.md
```

---

## Team 1 – Modello

### Obiettivo
Definire l’intero modello chimico-fisico, inclusi:

- Tipologia e geometria del reattore
- Reazioni chimiche e parametri cinetici
- Proprietà ottiche e ambientali
- Degradazione del catalizzatore e sottoprodotti

### Output
File YAML in `input/`

- `reaction_model.yaml`
- `geometry.yaml`
- `catalyst.yaml`
- `optical_properties.yaml`
- `environment.yaml`

---

## Team 2 – Computazionale

### Obiettivo
Implementare i solver numerici che traducono i modelli scientifici in simulazioni digitali.

### Moduli

- `kinetics_solver.py`: risolve le ODE delle reazioni
- `dom_solver.py`: calcola il trasporto di fotoni
- `flow_solver.py`: esegue la simulazione fluidodinamica
- `coupler.py`: accoppia luce + flusso + reazione

### Output
Salvati in `output/` come YAML:

- `kinetic_output.yaml`
- `light_field.yaml`
- `flow_field.yaml`
- `reactor_simulation.yaml`

---

## Team 3 – Integrazione / Orchestrazione

### Obiettivo
Gestire l’intera pipeline in modo sequenziale, automatico e riproducibile.

### Tool

- `run_orchestration.py`: legge `orchestrator.yaml` e avvia i moduli
- `validate_inputs.py`: controlla la correttezza dei file YAML
- Logging, gestione errori e gestione degli output

---

## Requisiti Software

- Python ≥ 3.9
- Librerie: `PyYAML`, `NumPy`, `SciPy`, `subprocess`, `jsonschema`
- (Opzionali) Cantera, OpenFOAM, FEniCS, PHOTOREAC, MATLAB

---

## Come avviare la simulazione

```bash
cd orchestrator/
python run_orchestration.py
```

---

## Estendibilità

- Aggiunta di nuovi moduli (es. ottimizzazione, machine learning)
- Supporto per più geometrie e meccanismi cinetici
- Integrazione con esperimenti reali per validazione

---

## Licenza

Progetto riservato ad uso scientifico e didattico. Contattare il responsabile del gruppo per contributi.
