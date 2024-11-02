#include <iostream>

using namespace std;

class Entity
{
private:
    int health;
    int max_health;
    string name;
    int damage;
public:
    Entity() : name("bezNazwy"), health(100), max_health(100), damage(10) {}

    Entity(const string& name) : name(name), health(100), max_health(100), damage(10) {}

    void lowerHealth(int amount)
    {
        if (amount < 0) { amount *= -1; }

        health -= amount;
        if (health < 0) { health = 0; }
    }
    void addHealth(int amount)
    {
        if (amount < 0) { amount *= -1; }

        health += amount;
        if (health > max_health) { health = max_health; }
    }

    string getName() const {
        return name;
    }
    int getHealth() const {
        return health;
    }
    int getMaxHealth() const {
        return max_health;
    }
    int getDamage() const {
        return damage;
    }

};

class Player : Entity
{
private:
    int metal;
    int oxygen;
public:
    Player() : Entity(), oxygen(100), metal(50) {}

    Player(string name, int oxy, int mtl)
        : Entity(name) {
        oxygen = oxy, metal = mtl;
    }

    int getMetal() const
    {
        return metal;
    }

    int getOxygen() const
    {
        return oxygen;
    }
    void displayPlayerInfo() const
    {
        std::cout << "Player name: " << getName() << "\n"
            << "Health: " << getHealth() << "\n"
            << "Oxygen: " << oxygen << "\n";
    }
    void rest()
    {
        addHealth(10);
        oxygen -= 5;
        if (oxygen > 100) oxygen = 100;
    }

    void lowerOxygen(int amount)
    {
        if (amount < 0) { amount *= -1; }

        oxygen -= amount;
        if (oxygen < 0) { oxygen = 0; }
    }
    void addOxygen(int amount)
    {
        if (amount < 0) { amount *= -1; }

        oxygen += amount;
    }
    void addMetal(int amount)
    {
        if (amount < 0) { amount *= -1; }

        metal += amount;
    }
};

class Game {
private:
    Player player;
public:
    Game(string playerName) {
        player = Player(playerName, 100, 0);
    }
    void startGame() {
        cout << "-------------------------------------" << endl;
        cout << "Rozbiles sie na Ksiezycu!" << endl;
        cout << "Twoim zadaniem jest przetrwanie i zdobycie wystarczajaco duzo surowcow, by zbudowac statek do domu." << endl;
        cout << "Uwazaj na zapasy swojego tlenu, bez niego nie mozesz kontynuowac gry." << endl;
        cout << "Powodzenia!" << endl;
        cout << "-------------------------------------" << endl;

        bool isGameRunnig = true;
        char playerChoice;

        player.displayPlayerInfo();

        while (isGameRunnig) {
            printMainMenu();
            cin >> playerChoice;
            switch (playerChoice) {
            case '1':

                break;
            case '2':
                break;
            case '3':
                break;
            case '4':
                break;
            case '0':
                break;
            default:
                break;
            }
        }
    }
    void printMainMenu() {
        cout << "Co chesz zrobic?\n";
        cout << "-------------------------------------" << endl;
        cout << "1. Sprawdz swoj stan.\n";
        cout << "2. Odpocznij.\n";
        cout << "3. Szukaj zasobow.\n";
        if (player.getMetal() > 50) {
            cout << "4. Zbuduj statek.\n";
        }
        cout << "0. Skoncz gre!!!!\n";
        cout << "-------------------------------------" << endl;
    }
};

int main()
{
    Player player("imie", 100, 0);
    player.lowerOxygen(20);
    player.displayPlayerInfo();

    return 0;
}
