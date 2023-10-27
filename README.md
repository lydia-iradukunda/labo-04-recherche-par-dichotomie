/* ---------------------------
Laboratoire : 04
Autrice : IRADUKUNDA Lydia
Date : 22.10.2023
But : Recherche par dichotomie 
Remarque(s) : J'ai personnellement eu des soucis par rapport à cLion
--------------------------- */
#include <iostream>  // pour les entrées et les sorties
#include <cstdlib>  //  pour générer des nombres aléatoires

//Fonction pour la Recherche Dichotomique
int main() {
    int inferieure, superieure, nombre;

    std::cout << "Entrez la borne inferieure : ";
    std::cin >> inferieure;
    std::cout << "Entrez la borne superieure : ";
    std::cin >> superieure;

    //Choisir les bornes et l'utilisateur va les saisir correctement
    if (inferieure >= superieure) {
        std::cout << "Les limites sont dans le mauvais ordre." << std::endl;
        return 1;
    }

    //Essayer de trouver un nombre dans l'intervalle donné grâce à des questions oui-non.
    std::cout << "Veuillez choisir un nombre , puis repondre aux questions par 'o' ou 'n'." << std::endl;

    //Utiliser mode jeu ou test
    char mode;
    std::cout << "Mode jeu ou mode test ? Veuillez repondre par 'j' ou 't' : ";
    std::cin >> mode;

    if (mode == 't') {
        std::cout << "Entrez le nombre que vous avez choisi : ";
        std::cin >> nombre;

        if (nombre < inferieure || nombre > superieure) {
            std::cout << "Le nombre choisi n'est pas dans l'intervalle spécifié." << std::endl;
            return 1;
        }
    }
//Utisation des nombres aléatoires
    bool aleatoire = false;
    if (mode == 'j') {
        char utiliseRand;
        std::cout << "Utiliser la méthode rand() pour le choix de X (o/n) ? ";
        std::cin >> utiliseRand;
        aleatoire = (utiliseRand == 'o');
    }
//Passage dans la boucle WHILE
    int repetition = 0;
    int devine;

    while (true) {
        if (repetition) {
            devine = rand() % (superieure - inferieure + 1) + inferieure;
        } else {
            devine = (inferieure + superieure) / 2;
        }

        char response;
        std::cout << repetition + 1 << ". Le nombre est-il plus petit ou egal a " << devine << " ? ";
        std::cin >> response;
        if (response == 'o') {
            superieure = devine;
        } else {
            inferieure = devine + 1;
        }

        repetition++;

        if (superieure <= inferieure) {
            break;
        }
    }

    std::cout << "Le nombre choisi est " << inferieure << std::endl;
    std::cout << "Nombre d'iterations : " << repetition << std::endl;

    return 0;
}
//Fin du programme
