# Блок-схема Блэкджека

```mermaid
flowchart TD
    Start([Начало]) --> Init[Инициализация: x, игрок=, крупье=]
    Init --> LoopInit[Цикл: 2 итерации]
    LoopInit --> RandP[игрок.append(randint(1,11))]
    RandP --> RandD[крупье.append(randint(1,11))]
    RandD --> LoopInit
    LoopInit --> OutCards[Вывод: «Ваши карты», игрок]
    OutCards --> InDec[Ввод: решение (1/2)]
    InDec --> CheckDec{решение == 1 и sum(игрок) < 21?}
    CheckDec -- Да --> GetCard[карта = randint(1,11)]
    GetCard --> CheckDup1{игрок.count(карта)+крупье.count(карта) == 4?}
    CheckDup1 -- Да --> GetCard
    CheckDup1 -- Нет --> AppendP[игрок.append(карта)]
    AppendP --> InDec
    CheckDec -- Нет --> CheckDealer{sum(крупье) < 13?}
    CheckDealer -- Да --> GetCardD[карта = randint(1,11)]
    GetCardD --> CheckDup2{игрок.count(карта)+крупье.count(карта) == 4?}
    CheckDup2 -- Да --> GetCardD
    CheckDup2 -- Нет --> AppendD[крупье.append(карта)]
    AppendD --> CheckDealer
    CheckDealer -- Нет --> CheckDraw{sum(игрок)>21 и sum(крупье)>21 или sum(игрок)==sum(крупье)?}
    CheckDraw -- Да --> OutDraw[Вывод: «Ничья»]
    CheckDraw -- Нет --> CheckWin{sum(игрок)>sum(крупье) и sum(игрок)<22 или sum(крупье)>21?}
    CheckWin -- Да --> OutWin[Вывод: «Вы победили...»]
    OutWin --> ModXWin{x < 10000?}
    ModXWin -- Да --> XAdd[x += 100000]
    ModXWin -- Нет --> XMul[x *= 2]
    XAdd --> OutFinal
    XMul --> OutFinal
    CheckWin -- Нет --> OutLose[Вывод: «Вы отсосали...»]
    OutLose --> XDiv[x /= 2]
    XDiv --> OutFinal
    OutDraw --> OutFinal
    OutFinal[Вывод: карты игрока, крупье, x] --> End([Конец])

```
