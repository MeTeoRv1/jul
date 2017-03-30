#include <stdlib.h>
#include <unistd.h>

void	ft_ecrire_caractere(char c)
{
	write(1, &c, 1);
}

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
