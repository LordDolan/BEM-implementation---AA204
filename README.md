# BEM para Turbinas Eólicas — AA-204

Implementação em Python do método **Blade Element Momentum (BEM)** para projeto e análise de uma turbina eólica de eixo horizontal, feita para a disciplina **AA-204 — Aerodinâmica de Asas Rotativas**.

## O que tem no notebook

- Projeto da pá pelo **rotor ótimo de Glauert** (corda e torção)
- Seleção da polar do aerofólio **S834** pelo número de Reynolds
- Extensão pós-estol de **Viterna-Corrigan**
- **BEM** sem correção, com correção de ponta de **Prandtl** e com correção de **Glauert** para alta indução
- Correção **3D/rotacional** de Chaviaropoulos & Hansen
- Análise **off-design** ($C_P$ e $C_T$ em função do TSR)

## Como rodar

```bash
pip install numpy scipy pandas matplotlib
```

1. Coloque o arquivo da polar `Airfoil_S834.txt` (formato UIUC) na sua máquina.
2. No notebook, ajuste a variável `caminho` para o local desse arquivo.
3. Rode as células em ordem.

## Referências

- Hansen — *Aerodynamics of Wind Turbines*
- Sørensen — *General Momentum Theory for Horizontal Axis Wind Turbines*
- Schaffarczyk — *Introduction to Wind Turbine Aerodynamics*
- Viterna & Corrigan (1982)
- Chaviaropoulos & Hansen (2000)
- Notas e slides de aula — AA-204

## Autor

João Vicente Rosal Giovanneti Daros
