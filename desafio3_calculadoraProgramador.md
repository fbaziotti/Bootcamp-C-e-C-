#include <stdio.h>
#include <stdlib.h>

/*chamar uma função vzia onde será realizada a operação
de divisor por 2 afim de obter um número binário*/


void binario(int decimal){
    if(decimal == 0){
        printf("%d", decimal);
    }else{
        binario(decimal/2);
        printf("%d", decimal%2);
    }

}

int main(){
    
    printf("*****CALCULADORA DO PROGRAMADOR\n*****");
    printf("CONVERTE UMA ENTRADA DECIMAL PARA HEXADECIMAL, OCTAL E BINARIO\n");
    
    int decimal;
    printf("Digite um Numero Decimal: ");
    scanf("%d", &decimal);
    
    printf("Valor - Hexadecimal: %x, Octal: %o e Binario: ", decimal, decimal);
    binario(decimal);

    return 0;
}