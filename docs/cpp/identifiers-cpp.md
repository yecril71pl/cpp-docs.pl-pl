---
title: Identyfikatory (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- decorated names
- decorated names, about decorated names
- identifiers, C++
- white space, in C++ identifiers
- identifiers [C++]
ms.assetid: 03a0dfb1-4530-4cdf-8295-5ea4dca4c1b8
ms.openlocfilehash: 61ca021a8f41074dcef6bf9df2e5683ede98deee
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222429"
---
# <a name="identifiers-c"></a>Identyfikatory (C++)

Identyfikator jest sekwencja znaków używany do określenia jednej z następujących czynności:

- Nazwa zmiennej lub obiektu

- Klasy, struktury lub nazwa związku

- Nazwa wymienionego typu

- Element członkowski klasy, struktury, Unii lub wyliczenie

- Funkcja lub funkcji składowej klasy

- Nazwa TypeDef

- Nazwa etykiety

- Nazwa makra

- Parametr makra

Następujące znaki są dozwolone jako dowolny znak identyfikatora:

```
_ a b c d e f g h i j k l m
n o p q r s t u v w x y z
A B C D E F G H I J K L M
N O P Q R S T U V W X Y Z
```

Określone zakresy uniwersalne nazwy znaków są również dozwolone w identyfikatorze.  Nazwę znaki uniwersalne w identyfikatorze nie może wyznaczyć znaku kontrolnego lub znaków w zestawie znaków podstawowego źródła. Aby uzyskać więcej informacji, zobacz [zestawów znaków](../cpp/character-sets.md). Te Unicode kod punktu liczb są dozwolone zakresy jako uniwersalne nazwy znaków dowolny znak w identyfikatorze:

- 00A8, 00AA, 00AD, 00AF, 00B2 00B5, 00B7 00BA 00BC 00BE, D 00C 0-00 6, 8-00F6 00D, 00F8 00FF 02FF 0100, 0370 167F, D 1681 180, 180F 1DBF, 1E00 1FFF, 200B 200D, 202A 202E, 2040 203F, 2054, 206F 2060, 20CF 2070, 218F 2100, 2460-24FF, 2776 2793, 2C 00-2DFF, 2E80 2FFF, 3004 3007, 3021 302F, 3031 303F, 3040-D7FF F900 FD3D, FD40 FDCF, FDF0 FE1F, FE30 FE44, FE47 FFFD 10000 1FFFD, 20000 2FFFD, 40000 4FFFD, 80000 8FFFD, 50000 5FFFD, 70000 7FFFD, 30000 3FFFD, 60000 6FFFD, 9FFFD 90000, A0000 AFFFD, BFFFD B0000, C0000-CFFFD D0000-DFFFD E0000 EFFFD

Następujące znaki są dozwolone jako dowolny znak w identyfikatorze oprócz pierwszego:

```
0 1 2 3 4 5 6 7 8 9
```

Te Unicode kod punktu liczb są również dozwolone zakresy jako uniwersalne nazwy znaków dowolny znak w identyfikatorze oprócz pierwszego:

- 0300-036F, 1DC0-1DFF, 20D0-20FF, FE20-FE2F

**Microsoft Specific**

Tylko pierwsze 2048 znaków identyfikatorów Microsoft C++ są znaczące. Nazwy dla typów zdefiniowanych przez użytkownika są "dekorowane" przez kompilator, aby zachować informacje o typie. Wynikowe nazwę, w tym informacje o typie nie może być dłuższe niż 2048 znaków. (Zobacz [nazwy dekorowane](../build/reference/decorated-names.md) Aby uzyskać więcej informacji.) Dostępne są następujące czynniki, które mogą mieć wpływ na długość identyfikatora dekorowanego:

- Czy identyfikator oznacza obiekt typu zdefiniowanego przez użytkownika lub typ pochodzi z typu zdefiniowanego przez użytkownika.

- Czy identyfikator oznacza funkcję lub typ wywodzący się z funkcji.

- Liczba argumentów funkcji.

Znak dolara `$` jest znakiem prawidłowym identyfikatorem w programie Microsoft C++ kompilatora (MSVC). MSVC pozwala również na używanie rzeczywiste znaki, które są reprezentowane przez dozwolone zakresy uniwersalne nazwy znaków w identyfikatorach. Aby korzystać z tych znaków, musisz zapisać plik przy użyciu pliku kodowania stronę kodową, która je zawiera.  Ten przykład przedstawia, jak rozszerzyć zarówno znaki i uniwersalne nazwy znaków mogą być używane zamiennie w kodzie.

```cpp
// extended_identifier.cpp
// In Visual Studio, use File, Advanced Save Options to set
// the file encoding to Unicode codepage 1200
struct テスト         // Japanese 'test'
{
    void トスト() {}  // Japanese 'toast'
};

int main() {
    テスト \u30D1\u30F3;  // Japanese パン 'bread' in UCN form
    パン.トスト();        // compiler recognizes UCN or literal form
}
```

Zakres znaków dozwolonych w identyfikatorze jest mniej restrykcyjna, podczas kompilowania C++sposób niezamierzony kodu. Identyfikatory w kodzie skompilowanym za pomocą/CLR powinien być zgodny [Standard ECMA-335: Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).

**END specyficzny dla Microsoft**

Pierwszy znak identyfikatora musi być znakiem alfabetycznym, wielką lub małą literą lub podkreśleniem ( **_** ). Ponieważ identyfikatory języka C++ jest uwzględniana wielkość liter `fileName` różni się od `FileName`.

Identyfikatory nie może być dokładnie tej samej pisowni i wielkości liter jak słowa kluczowe. Identyfikatory zawierające słowa kluczowe są dozwolone. Na przykład `Pint` jest dozwolonym identyfikatorem, mimo że zawiera on **int**, które jest słowem kluczowym.

Użycie dwóch podkreślników ( **__** ) jest zarezerwowany dla identyfikatora lub pojedynczego wiodącego podkreślnika, a po nim wielkiej litery C++ implementacje we wszystkich zakresach. Należy unikać używania jednego wiodącego podkreślenia następuje mała litera dla nazw z zakresem pliku z powodu możliwych konfliktów z bieżącym lub przyszłymi zarezerwowanymi identyfikatorami.

## <a name="see-also"></a>Zobacz także

[Konwencje leksykalne](../cpp/lexical-conventions.md)
