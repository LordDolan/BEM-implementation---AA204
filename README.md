# Implementação de BEM para Turbinas Eólicas — AA-204

Implementação em Python do método **Blade Element Momentum (BEM)** para o projeto e a análise aerodinâmica de uma turbina eólica de eixo horizontal, desenvolvida na disciplina **AA-204 — Aerodinâmica de Asas Rotativas**.

O notebook faz o projeto da pá pelo **rotor ótimo de Glauert** e depois avalia essa geometria com o BEM, com e sem correções, no ponto de projeto e fora dele (*off-design*).

## Conteúdo

| Arquivo | Descrição |
|---|---|
| `Implementacao_1.ipynb` | Notebook com todo o projeto e a análise |

## O que o código faz

1. **Dados de entrada**: TSR, velocidade do vento, raio da pá, raio do cubo, número de pás e densidade do ar.
2. **Reynolds inicial**: estimativa de uma corda típica (Manwell et al., com $C_l \approx 1$) para calcular o Reynolds a 75% do raio.
3. **Leitura da polar (S834)**: lê o arquivo `.txt` do UIUC, que tem vários blocos de Reynolds, e escolhe o bloco mais próximo do Reynolds calculado.
4. **Ponto ótimo do aerofólio**: ângulo de ataque de máxima razão $C_l/C_d$.
5. **Rotor ótimo de Glauert**: distribuição de corda, torção e solidez ao longo da pá, e curva de $C_p$ teórico em função do TSR.
6. **Atualização do Reynolds**: recalcula o Reynolds com a corda real de projeto a 75% do raio e reseleciona a polar.
7. **Validação do projeto**: gráficos comparáveis às figuras de Sørensen (Figs. 5.2 e 5.3) e Schaffarczyk (Fig. 5.6).
8. **Extensão pós-estol (Viterna-Corrigan)**: estende a polar até 90°.
9. **BEM**, em três versões:
   - sem correções;
   - com correção de perda de ponta de **Prandtl**;
   - com Prandtl + correção de **Glauert** para rotor fortemente carregado ($a > 1/3$).

   As três incluem a correção **3D/rotacional** de Chaviaropoulos & Hansen (2000) na polar.
10. **Desempenho no ponto de projeto**: empuxo, potência, $C_T$ e $C_P$, além das distribuições de $a$, $a'$ e $\alpha$ ao longo da pá.
11. **Análise off-design**: curvas $C_P \times TSR$ e $C_T \times TSR$ para a geometria fixa.

## Como rodar

### Requisitos

- Python 3.10+
- Bibliotecas: `numpy`, `scipy`, `pandas`, `matplotlib`

```bash
pip install numpy scipy pandas matplotlib
```

> O código usa `np.trapezoid`, que exige **NumPy 2.0 ou mais recente**. Em versões antigas, troque por `np.trapz`.

### Dados do aerofólio

O notebook precisa do arquivo de polar do aerofólio **S834** no formato do UIUC (`Airfoil_S834.txt`). O caminho está fixo no código:

```python
caminho = r"C:\Users\JVicenteRGD\Documents\Aerodinamica de Asas Rotativas\Dados de Aerofolio\Airfoil_S834.txt"
```

Ajuste essa linha para o local do arquivo na sua máquina antes de executar.

### Execução

Abra o notebook no Jupyter ou no VS Code e rode as células **em ordem**, de cima para baixo. Cada etapa usa variáveis criadas nas anteriores.

## Parâmetros de projeto

Definidos na célula de dados de entrada. Altere-os para estudar outras configurações:

| Parâmetro | Variável | Valor atual |
|---|---|---|
| Tip Speed Ratio | `TSR` | 6 |
| Velocidade do vento | `V_0` | 10 m/s |
| Raio da pá | `R` | 20 m |
| Raio do cubo | `R_cubo` | 4 m |
| Número de pás | `B` | 4 |
| Densidade do ar | `rho` | 1,225 kg/m³ |

## Referências

- HANSEN, M. O. L. *Aerodynamics of Wind Turbines*. Earthscan.
- SØRENSEN, J. N. *General Momentum Theory for Horizontal Axis Wind Turbines*. Springer, 2016.
- SCHAFFARCZYK, A. P. *Introduction to Wind Turbine Aerodynamics*. Springer.
- MANWELL, J. F.; McGOWAN, J. G.; ROGERS, A. L. *Wind Energy Explained: Theory, Design and Application*. 2. ed. Wiley, 2009.
- VITERNA, L. A.; CORRIGAN, R. D. Fixed pitch rotor performance of large horizontal axis wind turbines. *Large Horizontal-Axis Wind Turbines*, NASA, 1982.
- CHAVIAROPOULOS, P. K.; HANSEN, M. O. L. Investigating Three-Dimensional and Rotational Effects on Wind Turbine Blades by Means of a Quasi-3D Navier-Stokes Solver. *Journal of Fluids Engineering*, v. 122, p. 330–336, 2000.
- Notas e slides de aula — AA-204.

## Autor

João Vicente Rosal Giovanneti Daros
