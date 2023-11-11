#include <iostream>
#include <vector>
#include <ctime>

const int BOARD_SIZE = 5;
const int NUM_SHIPS = 3;

class Ship {
public:
    int size;
    std::vector<std::pair<int, int>> coordinates;

    Ship(int s) : size(s) {}
};

class Player {
public:
    std::string name;
    std::vector<std::vector<char>> board;
    std::vector<Ship> ships;

    Player(std::string n) : name(n) {
        board = std::vector<std::vector<char>>(BOARD_SIZE, std::vector<char>(BOARD_SIZE, '~'));
    }

    void placeShips() {
        for (int i = 0; i < NUM_SHIPS; i++) {
            int shipSize = i + 2; // Tamanhos de navios de 2 a 4
            Ship ship(shipSize);

            int x, y, orientation;
            std::cout << name << ", posicione um navio de tamanho " << shipSize << " (x y orientacao): ";
            std::cin >> x >> y >> orientation;

            for (int j = 0; j < shipSize; j++) {
                if (orientation == 0) {
                    ship.coordinates.push_back(std::make_pair(x + j, y));
                } else {
                    ship.coordinates.push_back(std::make_pair(x, y + j));
                }
            }

            ships.push_back(ship);
            updateBoard();
            printBoard();
        }
    }

    void updateBoard() {
        for (auto& ship : ships) {
            for (auto& coord : ship.coordinates) {
                int x = coord.first;
                int y = coord.second;
                board[y][x] = 'S';
            }
        }
    }

    void printBoard() {
        std::cout << "  ";
        for (int i = 0; i < BOARD_SIZE; i++) {
            std::cout << i << " ";
        }
        std::cout << std::endl;

        for (int i = 0; i < BOARD_SIZE; i++) {
            std::cout << i << " ";
            for (int j = 0; j < BOARD_SIZE; j++) {
                std::cout << board[i][j] << " ";
            }
            std::cout << std::endl;
        }
    }

    bool checkHit(int x, int y) {
        for (auto& ship : ships) {
            for (auto& coord : ship.coordinates) {
                if (coord.first == x && coord.second == y) {
                    coord.first = -1; // Marcar como atingido
                    board[y][x] = 'X'; // Marcar no tabuleiro
                    return true;
                }
            }
        }
        board[y][x] = 'O'; // Marcar como água
        return false;
    }
};

int main() {
    srand(time(0));

    Player player1("Jogador 1");
    Player player2("Jogador 2");

    player1.placeShips();
    player2.placeShips();

    Player* currentPlayer = &player1;
    Player* opponent = &player2;

    while (true) {
        std::cout << currentPlayer->name << ", é a sua vez de atirar (x y): ";
        int x, y;
        std::cin >> x >> y;

        bool hit = opponent->checkHit(x, y);
        currentPlayer->printBoard();

        if (hit) {
            std::cout << "Acertou!" << std::endl;
        } else {
            std::cout << "Água..." << std::endl;
        }

        bool allShipsSunk = true;
        for (auto& ship : opponent->ships) {
            for (auto& coord : ship.coordinates) {
                if (coord.first != -1) {
                    allShipsSunk = false;
                    break;
                }
            }
        }

        if (allShipsSunk) {
            std::cout << currentPlayer->name << " venceu!" << std::endl;
            break;
        }

        std::swap(currentPlayer, opponent);
    }

    return 0;