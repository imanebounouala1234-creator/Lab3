# Lab3
def calcul_reduction(prix, est_etudiant, fidelite_ans):
    reduction_totale = 0
    
    # Règle 1: Réduction de 10 % pour les étudiants
    if est_etudiant:
        reduction_totale += prix * 0.10
        print(f"- Remise étudiant (10%): -{prix * 0.10:.2f}€")

    # Règle 2: Réduction de 15 % pour la fidélité (>= 5 ans)
    if fidelite_ans >= 5:
        reduction_totale += prix * 0.15
        print(f"- Remise fidélité (15%): -{prix * 0.15:.2f}€")

    # Règle 3: Réduction supplémentaire de 5€ si prix > 100€
    if prix > 100:
        reduction_totale += 5
        print(f"- Remise bonus (>100€): -5.00€")

    # Calcul du prix final
    prix_final = prix - reduction_totale

    # Règle 4: Ne pas descendre en dessous de 0
    if prix_final < 0:
        prix_final = 0
        
    return prix_final

# --- Programme Principal ---
try:
    p_initial = float(input("Entrez le prix initial du produit (€) : "))
    
    if p_initial <= 0:
        print("Erreur: Le prix doit être supérieur à 0.")
    else:
        reponse_etudiant = input("Êtes-vous étudiant ? (oui/non) : ").lower()
        est_etud = (reponse_etudiant == "oui")
        
        ans_fidelite = int(input("Années de fidélité : "))

        print("\n--- Détails du calcul ---")
        p_final = calcul_reduction(p_initial, est_etud, ans_fidelite)
        
        print("-" * 25)
        print(f"PRIX INITIAL : {p_initial:.2f} €")
        print(f"PRIX FINAL   : {p_final:.2f} €")
        print("-" * 25)

except ValueError:
    print("Erreur: Veuillez saisir des chiffres valides.")
