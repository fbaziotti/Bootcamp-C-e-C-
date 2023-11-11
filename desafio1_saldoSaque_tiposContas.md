 //Bibliotecas do C++
#include <iostream>
#include <iomainp>
#include <string>

//Utilizar padrão std
using namespace std;

int main() {
    //Limitar as operações a duas casas decimais após o ponto
    cout << fixed << setprecision(2);
    
     //Tipos de clientes
    int tipoCliente;

    //Tipos de contas
    int tipoConta;

    //Declarando tarifas dos tipos de contas PF
    float tarifaCC = 12.49;
    float tarifaCS = 0;
    float tarifaCP = 1.90;
    float tarifaCI = 4.90;

    //Declarando tarifas dos tipos de contas PJ
    float tarifaCCJ = 54.49;
    float tarifaCSJ = 0;
    float tarifaCPJ = 8.90;
    float tarifaCIJ = 25.90;


    // Informação data da abertura de conta - PF e PJ integradas
    string dataAberturaCC = ("11/09/2012");
    string dataAberturaCS = ("23/05/2018");
    string dataAberturaCP = ("03/02/1985");
    string dataAberturaCI = ("16/04/2022");

    //Últimos depósitos realizados nas contas físicas
    float depCC = 150.56;
    float depCS = 3134.09;
    float depCP = 31.76;
    float depCI = 4787.99;

    //Últimos depósitos realizados nas contas jurídicas
    float depCCJ = 1500.56;
    float depCSJ = 31340.09;
    float depCPJ = 310.76;
    float depCIJ = 47870.99;

    //Saques CF
    float saqueCC;
    float saqueCS;
    float saqueCP;
    float saqueCI;

    //Saques CJ
    float saqueCCJ;
    float saqueCSJ;
    float saqueCPJ;
    float saqueCIJ;

    //Saldo final para quaisquer contas
    float saldoFinal;

    //opcao para casos de clientes física ou jurídica
    int opcao;
    int opcaoJ;

    cout << "Escolha: 1) conta fisica ou 2) juridica: ";
    cin >> tipoCliente;
    if (tipoCliente == 1){
        cout << "Conta Fisica\n";
        cout << "Deseja realizar operacao de saque em quais contas? \n";
        cout << "1) corrente\n";
        cout << "2) salario\n";
        cout << "3) poupanca\n";
        cout << "4) investimento\n";
        cin >> opcao;
    } else if (tipoCliente == 2) {
        cout << "Conta Juridica\n";
        cout << "Deseja realizar operacao de saque em quais contas? \n";
        cout << "1) corrente\n";
        cout << "2) salario\n";
        cout << "3) poupanca\n";
        cout << "4) investimento\n";
        cin >>opcaoJ;
    }
        switch(opcao) {
            //Escolha PF
            case 1:
            cout << "Conta corrente pf. Cliente desde: " << dataAberturaCC << endl;
            cout << "Informando sua taxa de operacao: " << tarifaCC << endl;
            cout << "Valor do saque desejado: ";
            cin >> saqueCC;
            saldoFinal = depCC - tarifaCC - saqueCC;
            if (saldoFinal >= 0){
                cout << "Saldo final positivo: " << saldoFinal << endl;
            }
            else {
                cout << "Valor acima do esperado!!! Saldo total positivo eh: " << depCC - tarifaCC;
            }
            break;

            case 2:
            cout << "Conta salario pj. Cliente desde: " << dataAberturaCS << endl;
            cout << "Informando sua taxa de operacao: " << tarifaCS << endl;
            cout << "Valor do saque desejado: ";
            cin >> saqueCS;
            saldoFinal = depCS - tarifaCS - saqueCS;
            if (saldoFinal >= 0){
                cout << "Saldo final positivo: " << saldoFinal << endl;
            }
            else {
                cout << "Valor acima do esperado!!! Saldo total positivo eh: " << depCS - tarifaCS;
             }
            break;

            case 3:
            cout << "Conta poupanca pf. Cliente desde: " << dataAberturaCP << endl;
            cout << "Informando sua taxa de operacao: " << tarifaCP << endl;
            cout << "Valor do saque desejado: ";
            cin >> saqueCP;
            saldoFinal = depCP - tarifaCP - saqueCP;
            if (saldoFinal >= 0){
                cout << "Saldo final positivo: " << saldoFinal << endl;
            }
            else {
                cout << "Valor acima do esperado!!! Saldo total positivo eh: " << depCP - tarifaCP;
             }
            break;

            case 4:
            cout << "Conta investimento pj. Cliente desde: " << dataAberturaCI << endl;
            cout << "Informando sua taxa de operacao: " << tarifaCI << endl;
            cout << "Valor do saque desejado: ";
            cin >> saqueCI;
            saldoFinal = depCI - tarifaCI - saqueCI;
            if (saldoFinal >= 0){
                cout << "Saldo final positivo: " << saldoFinal << endl;
            }
            else {
                cout << "Valor acima do esperado!!! Saldo total positivo eh: " << depCI - tarifaCI;
             }
            break;
         }
         switch(opcaoJ) {
            //Escolha PJ
            case 1:
            cout << "Conta corrente pj\n";
            cout << "Informando sua taxa de operacao: " << tarifaCCJ << endl;
            cout << "Valor do saque desejado: ";
            cin >> saqueCCJ;
            saldoFinal = depCCJ - tarifaCCJ - saqueCCJ;
            if (saldoFinal >= 0){
                cout << "Saldo final positivo: " << saldoFinal << endl;
            }
            else {
                cout << "Valor acima do esperado!!! Saldo total positivo eh: " << depCCJ - tarifaCCJ;
            }
            break;

            case 2:
            cout << "Conta salario pj. Cliente desde: " << dataAberturaCS << endl;
            cout << "Informando sua taxa de operacao: " << tarifaCSJ << endl;
            cout << "Valor do saque desejado: ";
            cin >> saqueCSJ;
            saldoFinal = depCSJ - tarifaCSJ - saqueCSJ;
            if (saldoFinal >= 0){
                cout << "Saldo final positivo: " << saldoFinal << endl;
            }
            else {
                cout << "Valor acima do esperado!!! Saldo total positivo eh: " << depCSJ - tarifaCSJ;
             }
            break;

            case 3:
            cout << "Conta poupanca pf. Cliente desde: " << dataAberturaCP << endl;
            cout << "Informando sua taxa de operacao: " << tarifaCPJ << endl;
            cout << "Valor do saque desejado: ";
            cin >> saqueCPJ;
            saldoFinal = depCPJ - tarifaCPJ - saqueCPJ;
            if (saldoFinal >= 0){
                cout << "Saldo final positivo: " << saldoFinal << endl;
            }
            else {
                cout << "Valor acima do esperado!!! Saldo total positivo eh: " << depCPJ - tarifaCPJ;
             }
            break;

            case 4:
            cout << "Conta investimento pj. Cliente desde: "<<dataAberturaCI<<endl;
            cout << "Informando sua taxa de operacao: " << tarifaCIJ << endl;
            cout << "Valor do saque desejado: ";
            cin >> saqueCIJ;
            saldoFinal = depCIJ - tarifaCIJ - saqueCIJ;
            if (saldoFinal >= 0){
                cout << "Saldo final positivo: " << saldoFinal << endl;
            }
            else {
                cout << "Valor acima do esperado!!! Saldo total positivo eh: " << depCIJ - tarifaCIJ;
             }
            break;
         }
         return 0;
     } 
