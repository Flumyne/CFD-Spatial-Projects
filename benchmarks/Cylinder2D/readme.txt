1. Géométrie (CAO : Design Modeler)
  Domaine : rectangle de 20D (longueur) × 10D (hauteur).
  Cylindre : placé au centre, diamètre D = 0.01 m.
  Construction lines : ajoutées dans la zone de sillage pour permettre un raffinement local.

2. Cas 1 – Simulation laminaire (Re = 1000)
  Paramètres physiques
    Fluide : air, ρ = 1.225 kg/m³, μ = 1.789×10⁻⁵ Pa·s.
    Diamètre cylindre : D = 0.01 m.
    Vitesse entrée : U∞ = 1.47 m/s → Re ≈ 1000.
    Régime attendu : incompressible, instationnaire (vortex de Von Kármán).

  Maillage
    Type : quadrilatères.
    Taille cellule globale : 0.0025 m.
    Raffinement dans le sillage : 0.0005 m.
    Nombre total de cellules : 25 457.
    Qualité :
      Max aspect ratio = 2.73.
      Min element quality = 0.51.

  Paramètres CFD
    Modèle : Laminar.
    Conditions limites :
      Inlet : Velocity-inlet, U∞ = 1.47 m/s.
      Outlet : Pressure-outlet.
      Haut/bas : Symmetry.
      Cylindre : Wall (no slip).
    Solveur : SIMPLEC, discrétisation 2nd ordre.
    Initialisation : Hybrid.
    Pas de temps :
      Strouhal théorique : St = 0.198 (1 − 19.7/Re).
      St ≈ 0.2 → f ≈ 29.4 Hz → période ≈ 0.034 s.
      Δt choisi = 0.001 s (≈ 34 pas/oscillation).
      Durée simulation : 1 s (suffisant pour voir la stabilisation du vortex shedding).

  Post-traitement attendu
    Animation des vortex (iso-vorticité).
    Courbes Cd et Cl oscillant périodiquement.

3. Cas 2 – Simulation turbulente (Re = 10 000)
  Paramètres physiques
    Fluide : air, ρ = 1.225 kg/m³, μ = 1.789×10⁻⁵ Pa·s.  
    Diamètre cylindre : D = 0.01 m.
    Vitesse entrée : U∞ = 14.7 m/s → Re ≈ 10 000.
    Régime attendu : instationnaire turbulent.

  Maillage
    Type : quadrilatères avec inflation.
    Taille cellule globale : 0.0025 m.
    Raffinement par inflation :
      1ère couche = 1.5×10⁻⁵ m.
      15 couches, croissance 1.2.
      Nombre total de cellules : ~25 800.

  Paramètres CFD
    Modèle : k-ω SST.
    Conditions limites :
      Inlet : Velocity-inlet, U∞ = 14.7 m/s.
      Outlet : Pressure-outlet.
      Haut/bas : Symmetry.
      Cylindre : Wall (no slip).
    Solveur : SIMPLE, discrétisation 2nd ordre.
    Initialisation : Hybrid.
    Pas de temps :
      St ≈ 0.2 → f ≈ 294 Hz → période ≈ 0.0034 s.
      Δt choisi = 1×10⁻⁴ s (≈ 34 pas/oscillation).
      Durée simulation : 0.5 s.

    Post-traitement attendu
      Visualisation des vortex de Von Kármán plus serrés et plus instables qu’au cas laminaire.
      Extraction de Cd, Cl
