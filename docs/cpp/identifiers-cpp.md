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
ms.openlocfilehash: 2d16dd318cd42b6294ef60edf44a16ccaf47b99b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187676"
---
# <a name="identifiers-c"></a>Identyfikatory (C++)

Identyfikator to sekwencja znaków używana do określenia jednego z następujących elementów:

- Nazwa obiektu lub zmiennej

- Nazwa klasy, struktury lub związku

- Nazwa typu wyliczeniowego

- Składowa klasy, struktury, Unii lub wyliczenia

- Funkcja lub funkcja członkowska klasy

- Nazwa typedef

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

Niektóre zakresy uniwersalnych nazw znaków są również dozwolone w identyfikatorze.  Uniwersalna nazwa znaku w identyfikatorze nie może wyznaczyć znaku kontrolnego ani znaku w podstawowym zestawie znaków źródła. Aby uzyskać więcej informacji, zobacz [zestawy znaków](../cpp/character-sets.md). Te zakresy numerów punktów kodowych Unicode są dozwolone jako uniwersalne nazwy znaków dla dowolnego znaku w identyfikatorze:

- 00A8, 00AA, 00AD, 00AF, 00B2-00B5, 00B7-00BA, 00BC-00BE, 00C0-00D6, 00D8-00F6, 00F8-00FF, 0100-02FF, 0370-167F, 1681-180D, 180F-1DBF, 1E00-1FFF, 200B-200D, 202A-202E, 203F, 2060-206F, 2070 2054 2040 2776-2793 2E80-2FFF, 3004-3007, 3021-302F, 3031-303F, 3040-D7FF, F900-FD3D, FD40-FDCF, FDF0-FE1F, FE30-FE44, FE47-FFFD, 10000-1FFFD, 20 000-2FFFD, 30000-3FFFD, 40000-4FFFD, 50000-5FFFD, 60 000-6FFFD, 70000-7FFFD, 80000-8FFFD, 90000-9FFFD, A0000-AFFFD, B0000-BFFFD, C0000-CFFFD, D0000-DFFFD, E0000-EFFFD

Następujące znaki są dozwolone jako dowolny znak w identyfikatorze z wyjątkiem pierwszego:

```
0 1 2 3 4 5 6 7 8 9
```

Te zakresy numerów punktów kodowych Unicode są również dozwolone jako uniwersalne nazwy znaków dla dowolnego znaku w identyfikatorze z wyjątkiem pierwszego:

- 0300-036F, 1DC0-1DFF, 20D0-20FF, FE20-FE2F

**Specyficzne dla firmy Microsoft**

Tylko pierwsze 2048 znaków identyfikatorów Microsoft C++ są istotne. Nazwy typów zdefiniowanych przez użytkownika są "dekoracyjne" przez kompilator, aby zachować informacje o typie. Nazwa wynikowa, w tym informacje o typie, nie może być dłuższa niż 2048 znaków. (Aby uzyskać więcej informacji, zobacz [nazwy dekoracyjne](../build/reference/decorated-names.md) ). Czynniki, które mogą mieć wpływ na długość identyfikatora dekoracyjnego, to:

- Określa, czy identyfikator wskazuje obiekt typu zdefiniowanego przez użytkownika lub typ pochodzący od typu zdefiniowanego przez użytkownika.

- Określa, czy identyfikator oznacza funkcję, czy typ pochodzący z funkcji.

- Liczba argumentów funkcji.

Znak dolara `$` jest prawidłowym znakiem identyfikatora w kompilatorze języka Microsoft C++ (MSVC). MSVC umożliwia również korzystanie z rzeczywistych znaków reprezentowanych przez dozwolone Zakresy nazw uniwersalnych znaków w identyfikatorach. Aby użyć tych znaków, należy zapisać plik przy użyciu strony kodowej kodowania plików, która je zawiera.  Ten przykład pokazuje, jak znaki rozszerzone i uniwersalne nazwy znaków mogą być używane zamiennie w kodzie.

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

Zakres znaków dozwolony w identyfikatorze jest mniej restrykcyjny podczas kompilowania kodu C++/CLI. Identyfikatory w kodzie skompilowane przy użyciu/CLR powinny być zgodne ze [standardem ECMA-335: Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Pierwszy znak identyfikatora musi być znakiem alfabetycznym, wielką literą lub małą literą lub podkreśleniem ( **_** ). Ponieważ identyfikatory C++ są rozróżniane wielkości liter, `fileName` różnią się od `FileName` .

Identyfikatory nie mogą mieć dokładnie tej samej pisowni i wielkości liter co słowa kluczowe. Identyfikatory zawierające słowa kluczowe są prawne. Na przykład `Pint` jest to identyfikator prawny, nawet jeśli zawiera **`int`** , który jest słowem kluczowym.

Użycie dwóch kolejnych znaków podkreślenia ( **__** ) w identyfikatorze lub pojedynczy wiodący znak podkreślenia, po którym występuje Wielka litera, jest zarezerwowany dla implementacji języka C++ we wszystkich zakresach. Należy unikać używania jednego wiodącego podkreślenia, po którym następuje mała litera dla nazw z zakresem plików ze względu na potencjalne konflikty z bieżącymi lub przyszłymi identyfikatorami zarezerwowanymi.

## <a name="see-also"></a>Zobacz także

[Konwencje leksykalne](../cpp/lexical-conventions.md)
