import numpy as np
import matplotlib.pyplot as plt
import math

# ========================
# Funções de Constante de Tempo
# ========================

def tau_rc_teorico(R, C):
    return R * C

def tau_rl_teorico(R, L):
    return L / R

def tau_pelo_63(t_63):
    return t_63

def tau_pelo_37(t_37):
    return t_37

def tau_indireto(periodo):
    return periodo / 2.2

# ========================
# Funções de Resposta no Tempo
# ========================

# --- Circuito RC ---
def vc_carga(t, V, R, C):
    tau = R * C
    return V * (1 - np.exp(-t / tau))

def vc_descarga(t, V0, R, C):
    tau = R * C
    return V0 * np.exp(-t / tau)

# --- Circuito RL ---
def il_carga(t, V, R, L):
    tau = L / R
    I_final = V / R
    return I_final * (1 - np.exp(-t / tau))

def il_descarga(t, I0, R, L):
    tau = L / R
    return I0 * np.exp(-t / tau)

def vl(t, V, R, L):
    """Tensão no indutor durante a carga"""
    return V * np.exp(-t / (L / R))

# ========================
# Exemplo de Uso
# ========================

# Parâmetros (exemplo fictício)
R = 2000        # ohms
C = 0.22e-6     # F
L = 1.0         # H
V = 10.0        # V

# Intervalo de tempo para simulação
t = np.linspace(0, 0.005, 500)  # até 5 ms

# --- RC ---
Vc_c = vc_carga(t, V, R, C)
Vc_d = vc_descarga(t, V, R, C)

# --- RL ---
Il_c = il_carga(t, V, R, L)
Il_d = il_descarga(t, V/R, R, L)
Vl = vl(t, V, R, L)

# ========================
# Gráficos
# ========================

plt.figure(figsize=(12,6))

# RC
plt.subplot(1,2,1)
plt.plot(t*1000, Vc_c, label="Carga do Capacitor")
plt.plot(t*1000, Vc_d, label="Descarga do Capacitor", linestyle="--")
plt.title("Circuito RC - Vc(t)")
plt.xlabel("Tempo (ms)")
plt.ylabel("Tensão no Capacitor (V)")
plt.grid(True)
plt.legend()

# RL
plt.subplot(1,2,2)
plt.plot(t*1000, Il_c, label="Corrente de Carga (iL)")
plt.plot(t*1000, Il_d, label="Corrente de Descarga (iL)", linestyle="--")
plt.plot(t*1000, Vl, label="Tensão no Indutor (vL)", linestyle=":")
plt.title("Circuito RL - iL(t) e vL(t)")
plt.xlabel("Tempo (ms)")
plt.ylabel("Corrente (A) / Tensão (V)")
plt.grid(True)
plt.legend()

plt.tight_layout()
plt.show()

