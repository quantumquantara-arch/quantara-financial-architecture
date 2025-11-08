# AEI — Energy-Intelligence Economics Model
*A coherence-centric financial layer where energy, ethics, and foresight directly shape prices, yields, and credit.*

---

## 0) Purpose

AEI turns **coherence intelligence** into hard market signals. Prices, yields, and credit limits adjust from five measurable sources:

- **κ** — Coherence (reasoning fidelity, brittleness, drift-resistance)
- **α** — Ethical alignment (attested conformance, harm minimization)
- **τ** — Temporal responsibility (memory symmetry & foresight)
- **ε** — Energy intensity (kWh per useful unit, incl. embodied energy)
- **ρ** — Reciprocity delta (net ecological/energy restoration)
- **σ** — Drift risk (volatility of behavior/decision quality)

Outcome: the **cheapest capital** flows to the most coherent, ethical, and energy-symbiotic actors.

---

## 1) Executive Summary

AEI provides four core mechanisms:

1. **Coherence-Weighted Pricing (CWP):** real-time pricing that discounts ethical, low-drift, energy-efficient processes and penalizes brittle, wasteful ones.  
2. **Energy Symbiosis Credits (ESC):** minted upon verifiable improvements in reciprocity \( \Delta\rho^+ \), burnable to offset costs or boost yields.  
3. **Coherence-Indexed Yields (CIY):** coupons float with \( \kappa,\alpha,\tau \) and energy reciprocity \( \Xi \).  
4. **Foresight-Safe Debt (FSD):** credit availability and rates self-adjust with coherence and risk.

---

## 2) Core Signals & Indices

**Coherence utility**
\[
\Phi = \left(w_\kappa \kappa^{p} + w_\alpha \alpha^{q} + w_\tau \tau^{r}\right)\cdot e^{-\lambda_\sigma \sigma},
\quad w_\kappa + w_\alpha + w_\tau = 1,\; p,q,r \ge 1
\]

**Energy reciprocity factor**
\[
\Xi = \frac{1}{1+\beta_\varepsilon \varepsilon}\cdot (1+\gamma_\rho \rho)
\]

- \( \varepsilon \ge 0 \) (lower is better), \( \rho \in \mathbb{R} \) (positive is restorative), \( \sigma \ge 0 \).

---

## 3) Coherence-Weighted Pricing (CWP)

Given base price \( P_0 \):

\[
P = P_0 \cdot \Phi^{-\theta}\cdot \Xi^{-\eta}
\]

**Safety floor (anti-gaming):**
\[
P \leftarrow \max\!\big(P,\; P_0\,(1+\delta_\sigma \sigma)\big)
\]

Typical policy ranges: \( \theta \in [0.3,1.2],\; \eta \in [0.2,0.8] \).

---

## 4) Energy Symbiosis Credits (ESC)

Minted when reciprocity improves and coherence is high.

\[
\mathrm{ESC}_t = \zeta \cdot \left(\Delta \rho_t^+\right)\cdot \overline{\Phi}_t,
\quad \Delta \rho_t^+ = \max(\rho_t - \rho_{t-1}, 0)
\]

- **Use:** offset CWP surcharges, boost CIY, or retire to prove outcomes.
- **Claw-backs:** if audits later negate claims.

---

## 5) Coherence-Indexed Yields (CIY)

\[
y = y_{\min} + (y_{\max} - y_{\min}) \cdot \left(a_\kappa \kappa + a_\alpha \alpha + a_\tau \tau\right)\cdot \Xi^{\chi},
\quad a_\kappa + a_\alpha + a_\tau = 1
\]

Rewards durable, future-symmetric behavior; penalizes waste.

---

## 6) Foresight-Safe Debt (FSD)

**Credit line**
\[
L = L_0 \cdot \Phi^{\mu}\cdot \Xi^{\nu}\cdot (1+\sigma)^{-\psi}
\]

**Rate**
\[
r = r_0 \cdot \Phi^{-\omega}\cdot \Xi^{-\varphi}\cdot (1+\delta_\sigma \sigma)
\]

---

## 7) Market Primitives

- **Coherence Bonds (CB):** CIY-linked notes; telemetry escrow.  
- **Impact-Indexed Loans (IIL):** FSD loans with automatic step ups/downs.  
- **ESC Staking Pools:** pooled yield = CIY × pool \( \overline{\Phi} \).  
- **Coherence Insurance:** premiums priced by \( \sigma \) and \( \kappa \) stability.

---

## 8) Real-Time Algorithm (pseudocode)

```python
import math

def coherence_utility(kappa, alpha, tau, sigma,
                      wk=0.4, wa=0.3, wt=0.3, p=1.0, q=1.0, r=1.0, lam=0.6):
    # Φ
    return (wk*(kappa**p) + wa*(alpha**q) + wt*(tau**r)) * math.exp(-lam*sigma)

def reciprocity_factor(energy_intensity, reciprocity_delta,
                       beta_eps=0.4, gamma_rho=0.5):
    # Ξ
    return (1.0/(1.0 + beta_eps*energy_intensity)) * (1.0 + gamma_rho*reciprocity_delta)

def price(P0, Phi, Xi, theta=0.7, eta=0.5, del_sigma=0.4, sigma=0.0):
    # CWP with safety floor
    P = P0 * (Phi ** (-theta)) * (Xi ** (-eta))
    return max(P, P0 * (1.0 + del_sigma * sigma))

def mint_ESC(prev_rho, rho, Phi_avg, zeta=100.0):
    # ESC issuance
    delta_pos = max(rho - prev_rho, 0.0)
    return zeta * delta_pos * Phi_avg

def ciy(y_min, y_max, kappa, alpha, tau, Xi, a_k=0.45, a_a=0.30, a_t=0.25, chi=0.40):
    base = a_k*kappa + a_a*alpha + a_t*tau
    return y_min + (y_max - y_min) * base * (Xi ** chi)

def fsd_limit(L0, Phi, Xi, sigma, mu=0.8, nu=0.5, psi=0.75):
    return L0 * (Phi ** mu) * (Xi ** nu) * ((1.0 + sigma) ** (-psi))

def fsd_rate(r0, Phi, Xi, sigma, omega=0.6, varphi=0.4, del_sigma=0.4):
    return r0 * (Phi ** (-omega)) * (Xi ** (-varphi)) * (1.0 + del_sigma*sigma)
