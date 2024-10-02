# JOGO_DA_VELHA_INCIANTES.C
JOGO_DA_VELHA_INCIANTES.C

#include <stdio.h>
#include <string.h>


void forca(int estado){
    if(estado==0){
        printf("\n-------------");
        printf("\n|           |");
        printf("\n|");
        printf("\n|");
        printf("\n|");
        printf("\n|");
        printf("\n-");
    }else if (estado==1){
        printf("\n-------------");
        printf("\n|           |");
        printf("\n|           o");
        printf("\n|");
        printf("\n|");
        printf("\n|");
        printf("\n-");
    }else if (estado==2){
        printf("\n-------------");
        printf("\n|           |");
        printf("\n|           o");
        printf("\n|           |");
        printf("\n|");
        printf("\n|");
        printf("\n-");
    }else if (estado==3){
        printf("\n-------------");
        printf("\n|           |");
        printf("\n|           o");
        printf("\n|          -|");
        printf("\n|");
        printf("\n|");
        printf("\n-");
    }else if (estado==4){
        printf("\n-------------");
        printf("\n|           |");
        printf("\n|           o");
        printf("\n|          -|-");
        printf("\n|");
        printf("\n|");
        printf("\n-");
    }else if (estado==5){
        printf("\n-------------");
        printf("\n|           |");
        printf("\n|           o");
        printf("\n|          -|-");
        printf("\n|          /  ");
        printf("\n|");
        printf("\n-");
    }else if (estado==6){
        printf("\n-------------");
        printf("\n|           |");
        printf("\n|           o");
        printf("\n|          -|-");
        printf("\n|          / \\");
        printf("\n| Game Over!");
        printf("\n-");
    }
    
}

int main(void){
    //Variavel palavra secreta
    char p_sec[100];

    printf("JOGADOR 1:\n");
    printf("Palavra Secreta:\n");
    fgets(p_sec,100,stdin);
    printf("A palavra secreta: %s",
    p_sec);
    printf("A palavra tem %lu, caracteres",
    strlen(p_sec)-1);
    
    //A única coisa que ele fez é pular linhas 
    for(int i=0;i<30;i++){
        printf("\n");
    }

    //retira o ultimo caracacter de p_sec que está mais
    // devido a captura de ser fgtes()
    p_sec[strlen(p_sec)-1] ='\0';

    char p_tela[100];//Palavra da tela
    strcpy(p_tela, p_sec);//copia p_sec para tela
    
    //substitui a letra por '-' 
    for(int i=0; i<strlen(p_tela);i++){
        p_tela[i] = '_';
    }
    
    int erros = 0;
    while (1){
        //Imprimir a forca
        forca(erros);
        //Imprimir os underscores/underline 
        //'-' para cada letra da palavra secreta,
        // ou seja, p_tela
        printf("\n Advinhe: ");
        for(int i=0;i<strlen(p_tela);i++){
            printf("%c ",p_tela[i]);
        }
        // recebe a letra
        printf("\n Letra: ");
        char letra;
        scanf(" %c", &letra);//o espaço antes do " %c" é necessário para que não ocorra erros

        // se a letra esta correta atualizar a palavra na tela
        // e verifica se a letra esta correta.

        int sera_que_errou=1;//1=sim 0=não
        for(int i=0; i<strlen(p_tela);i++){
            if(letra==p_sec[i]){//se tiver certo atualiza
                p_tela[i] = letra;
                sera_que_errou =0;
            }
        }
        // se não incrementa erros
        if (sera_que_errou==1){
            erros++;
        }
        // verifica se o jogo acabou
        // verifica se ganhou
        // verifica se a palavra p_sec é igual a p_tela
        if(strcmp(p_tela,p_sec)==0){
            //Ganhou
            printf("\n Advinhe: ");
            for(int i=0;i<strlen(p_tela);i++){
                printf("%c ",p_tela[i]);
            }
            printf("\n Parabens abestado voce venceu!!!");
            break;
        }
        if(erros==6){
            //Perdeu
            forca(erros);
            break;
        }
        
    }
    
    
    return 0;
}
