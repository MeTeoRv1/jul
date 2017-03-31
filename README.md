#include <stdlib.h>
#include <unistd.h>


/**
 * \fn void ft_putchar(char c)
 * \brief Écrire un caractère
 *
 * \param c Le caractère a écrire.
 *
 * Écrire le caractère.
 */
void	ft_ecrire_caractere(char c)
{
	write(1, &c, 1);
}


/**
 * \fn int **init_tableau()
 * \brief Initialiser le tableau.
 *
 * Créer un tableau de 5 par 5.
 */
 
int	**init_tableau()
{
	int **tableau, i, j;

	tableau = malloc(sizeof(*tableau) * 5);
	for(i = 0; i < 5; i++)
	{
		tableau[i] = malloc(sizeof(**tableau) * 5);
		for(j = 0; j < 5; j++)
			tableau[i][j] = 0;
	}

	return(tableau);
}


/**
 * \fn void free_tableau(int **tableau)
 * \brief Liberez un tableau de la memoire.
 *
 * \param tableau Le tableau a liberer.
 *
 * Liberer la memoire prise par le tableau.
 */
 
void	free_tableau(int **tableau)
{
	int i = 4;
	while(i >= 0)
	{
		free(tableau[i]);
		i--;
	}
	free(tableau);
}

/**
 * \fn void afficher_tableau(int **tableau)
 * \brief Afficher un tableau.
 *
 * \param tableau Le tableau a afficher.
 *
 * Affiche un tableau sur la sortie standard.
 */

void	afficher_tableau(int **tableau)
{
	int i, j;

	for(i = 0; i < 5; i++)
	{
		for(j = 0; j < 5; j++)
		{
			ft_ecrire_caractere(tableau[i][j] + '0');
			if(j < 5 - 1)
				ft_ecrire_caractere(' ');
		}
		ft_ecrire_caractere('\n');
	}
}

/**
 * \fn void modifie(int **tableau)
 * \brief Modifier un tableau.
 *
 * \param tableau Le tableau a modifier.
 *
 * Modifie le caractere central d'un tableau.
 */

void	modifier_tableau(int **tableau)
{
	tableau[2][2] = 1;
}

int	main(void)
{
	int **tableau;

	tableau = init_tableau();
	afficher_tableau(tableau);
	ft_ecrire_caractere('\n');
	modifier_tableau(tableau);
	afficher_tableau(tableau);
	free_tableau(tableau);

	return(0);
}
