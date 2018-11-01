---
title: Deklaracje i definicje (C++)
ms.date: 11/04/2016
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: 1e76f636a6efd652ac629ad2f97f0b09f6171f9c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432117"
---
# <a name="declarations-and-definitions-c"></a>Deklaracje i definicje (C++)

Deklaracje wprowadzają nazwy w programie, na przykład nazwy zmiennych, przestrzenie nazw, funkcji i klas. Deklaracje również określić informacje o typie, a także innych charakterystyk obiekt, który jest został zadeklarowany. Nazwa musi być zadeklarowany, zanim będzie można używać; w języku C++ punktu, w którym jest zadeklarowany nazwa określa, czy jest widoczny w kompilatorze. Nie można odwołać się do funkcji lub klasy, która jest zadeklarowana w pewnym momencie później w jednostce kompilacji; Możesz użyć *Przekaż dalej deklaracje* Aby obejść to ograniczenie.

Definicje Określ, jaki kod lub dane opisuje nazwę. Kompilator wymaga definicji, aby można było przydzielić miejsce do magazynowania na rzecz, którą jest on zadeklarowany.

## <a name="declarations"></a>Deklaracje

Deklaracja wprowadza jedną lub więcej nazw do programu. Deklaracje może wystąpić więcej niż jeden raz w programie. W związku z tym klasy, struktury, wyliczenia, typy i innych typów zdefiniowanych przez użytkownika mogą być deklarowane dla każdej jednostki kompilacji. Ograniczenie dla tej deklaracji wielu polega na tym, że wszystkie deklaracje muszą być identyczne. Deklaracje również służyć jako definicje, chyba że deklaracji:

1. Jest prototyp funkcji (deklaracja funkcji za pomocą bez treści funkcji).

1. Zawiera **extern** specyfikator, ale inicjatora (obiektów i zmiennych) lub treści funkcji (funkcje). Oznacza to, że definicja nie jest w bieżącej jednostce tłumaczenia i zapewnia zewnętrznego powiązania nazwy.

1. To element członkowski danych statycznych w obrębie deklaracji klasy.

   Ponieważ elementy członkowskie danych statycznych klas są zmiennych dyskretnych współużytkowane przez wszystkie obiekty klasy, muszą być zdefiniowane i zainicjować poza deklaracją klasy. (Aby uzyskać więcej informacji na temat klas i składowych klasy, zobacz [klasy](../cpp/classes-and-structs-cpp.md).)

1. Jest deklaracji nazwy klasy nie następujące definicje, takich jak `class T;`.

1. Jest **typedef** instrukcji.

Przykłady deklaracji, które jest także definicjami:

```cpp
// Declare and define int variables i and j.
int i;
int j = 10;

// Declare enumeration suits.
enum suits { Spades = 1, Clubs, Hearts, Diamonds };

// Declare class CheckBox.
class CheckBox : public Control
{
public:
            Boolean IsChecked();
    virtual int     ChangeState() = 0;
};
```

Kilka deklaracji, które nie są definicjami są:

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

Nazwa jest uważany za zgłaszane natychmiast po jego deklaratora, ale przed jego Inicjator (opcjonalnie). Aby uzyskać więcej informacji, zobacz [punkt deklaracji](../cpp/point-of-declaration-in-cpp.md).

Deklaracje występują w *zakres*. Zakres kontroluje widoczność zgłoszonej nazwy i ewentualnie czas trwania zdefiniowanego obiektu. Aby uzyskać więcej informacji na temat reguł współdziałania zakresu z deklaracjami, zobacz [zakres](../cpp/scope-visual-cpp.md).

Deklaracja obiektu jest również definicją chyba że zawiera on **extern** Specyfikator klasy magazynowania opisany w [klasy magazynu](storage-classes-cpp.md). Deklaracja funkcji jest również definicją, chyba że jest prototypem. Prototyp jest nagłówkiem funkcji bez definiowania treści funkcji. Definicja obiektu powoduje alokację pamięci masowej i odpowiednie inicjowania dla tego obiektu.

## <a name="definitions"></a>Definicje

Definicja jest unikatowy specyfikacji obiektu lub zmiennej, funkcji, klasy lub modułu wyliczającego. Ponieważ definicje muszą być unikatowe, program może zawierać tylko jedną definicję dla elementu danego programu. Może to być połączenie wiele do jednego między deklaracje i definicje. Istnieją dwa przypadki, w których element programu może być deklarowane i definiowane nie:

1. Funkcja jest zadeklarowana, ale nigdy nie przywoływany z wywołania funkcji lub wyrażenie, które przyjmuje adres funkcji.

1. Klasa jest używana tylko w sposób, który nie wymaga być znane, jego definicji. Jednak klasy musi być zadeklarowany. Poniższy kod ilustruje takiej sytuacji:

    ```cpp
    // definitions.cpp
    class WindowCounter;   // Forward declaration; no definition

    class Window
    {
       // Definition of WindowCounter not required
       static WindowCounter windowCounter;
    };

    int main()
    {
    }
    ```

## <a name="see-also"></a>Zobacz także

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)<br/>
[Punkt deklaracji](../cpp/point-of-declaration-in-cpp.md)