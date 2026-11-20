# Final_Project_CS121
11/10/26

# UML

classDiagram

    class HasMenu {
        <<interface>>
        +menu() String
        +start() void
    }

    class Serializable {
        <<interface>>
    }

    class DailyGame {
        <<abstract>>
        #lastScore: int
        #played: boolean
        +DailyGame()
        +gameName(): String
        +menu(): String
        +start(): void
        +play(): int
        +getLastScore(): int
        #calcScore(): int
        #getInput(): String
    }

    class RNGdle {
        -currentRoll: String
        -medals: ArrayList
        -MAX_DIGITS: int
        +RNGdle()
        +main(): void
        +gameName(): String
        +menu(): String
        +start(): void
        +play(): int
        -chooseOption(choice): void
        -rollNumber(): String
        -shrinkRoll(digits): void
        -checkMedals(): void
        -hasConsecutive(): boolean
        -getRarity(score): String
        #calcScore(): int
    }

    class Wordle {
        -answer: String
        -wordList: ArrayList
        -guesses: ArrayList
        -MAX_GUESSES: int
        +Wordle()
        +main(): void
        +gameName(): String
        +menu(): String
        +start(): void
        +play(): int
        -chooseOption(choice): void
        -pickWord(): void
        -getGuess(): String
        -checkGuess(guess): String
        -displayBoard(): void
        -getMultiplier(): double
        #calcScore(): int
    }

    class User {
        <<abstract>>
        ~userName: String
        ~PIN: String
        +login(): boolean
        +login(userName, PIN): boolean
        +setUserName(userName): void
        +getUserName(): String
        +setPIN(PIN): void
        +getPIN(): String
        +getReport(): String
    }

    class Admin {
        -players: ArrayList
        +Admin()
        +getReport(): String
        +menu(): String
        +start(): void
        +start(players): void
        -viewPlayers(): void
        -editScore(): void
        -editStreak(): void
        -addPlayer(): void
        -removePlayer(): void
        -resetPIN(): void
    }

    class Player {
        -lifetimeScore: int
        -winStreak: int
        ~rngdle: RNGdle
        ~wordle: Wordle
        +Player()
        +Player(userName, PIN)
        +main(): void
        +menu(): String
        +start(): void
        -chooseOption(choice): void
        +addScore(points): void
        +getLifetimeScore(): int
        +getWinStreak(): int
        +setWinStreak(streak): void
        +setPin(): void
        +getReport(): String
    }

    class Game {
        -FILE_NAME: String
        ~players: ArrayList
        ~admin: Admin
        +Game()
        +main(): void
        +menu(): String
        +start(): void
        -chooseOption(choice): void
        -createPlayer(): void
        -loginAsPlayer(): void
        -loginAsAdmin(): void
        +loadPlayers(players): void
        +savePlayers(players): void
        +leaderboardReport(): void
        +loadSamplePlayers(): void
    }

    DailyGame ..|> HasMenu
    User ..|> HasMenu
    Game ..|> HasMenu
    User ..|> Serializable
    RNGdle --|> DailyGame
    Wordle --|> DailyGame
    Admin --|> User
    Player --|> User
    Player *-- "1" RNGdle
    Player *-- "1" Wordle
    Game o-- "1" Admin
    Game o-- "n" Player

  ```
