flowchart TD
  %% Definición de swimlanes
  subgraph Operaciones
    A1[Inicio del Proceso]
    A2[Recolectar indicadores de almacén]
    A3[Recolectar datos de rutas (TRESGUERRAS)]
  end
  subgraph IT_Dashboard
    B1[Actualizar Dashboard con datos]
    B2[Monitorear KPIs críticos]
  end
  subgraph Logística
    C1[Evaluar estado de rutas alternativas]
    C2{¿Ruta alternativa\nviable?}
    C3[Activar ruta alternativa]
    C4[Notificar a transportistas]
  end
  subgraph Dirección
    D1{¿Indicadores por encima\numbral de riesgo?}
    D2[Convocar Comité de Crisis]
    D3[Escalar a Dirección General]
  end
  subgraph Operaciones_Final
    Z1[Restaurar operaciones normales]
    Z2[Revisión y lecciones aprendidas]
    Z3[Fin del Proceso]
  end

  %% Conexiones internas
  A1 --> A2 --> A3 --> B1
  B1 --> B2 --> D1
  D1 -- No --> B2
  D1 -- Sí --> D2 --> C1
  C1 --> C2
  C2 -- Sí --> C3 --> C4 --> Z1
  C2 -- No --> D3 --> Z1
  Z1 --> Z2 --> Z3

  %% Feedback loop para mejora continua
  Z2 --> A1
