---
title: Identyfikatory języka C
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
ms.openlocfilehash: 1f3abf304e6fda52e2571d0bccb8d4db5a414dfe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325666"
---
# <a name="c-identifiers"></a>Identyfikatory języka C

"Identyfikatory" lub "symbole" są nazwami dostarczanymi dla zmiennych, typów, funkcji i etykiet w programie. Nazwy identyfikatorów muszą różnić się pisownią i wielkością liter we wszystkich słowach kluczowych. Nie można używać słów kluczowych (C ani Microsoft) jako identyfikatorów; są one zarezerwowane do użytku specjalnego. Można utworzyć identyfikator, określając go w deklaracji zmiennej, typu lub funkcji. W tym przykładzie `result` jest identyfikatorem zmiennej integer i `main` i `printf` są nazwami identyfikatorów dla funkcji.

```
#include <stdio.h>

int main()
{
    int result;

    if ( result != 0 )
        printf_s( "Bad file handle\n" );
}
```

Po zadeklarowaniu można użyć identyfikatora w późniejszych instrukcjach programu, aby odwołać się do skojarzonej wartości.

W `goto` instrukcjach można używać specjalnego rodzaju identyfikatora o nazwie etykieta instrukcji. (Deklaracje są opisane w [deklaracjach i typach](../c-language/declarations-and-types.md) etykiet instrukcji są opisane w [instrukcjach goto i labeled](../c-language/goto-and-labeled-statements-c.md).)

## <a name="syntax"></a>Składnia

*Identyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*dowolny*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *niecyfrowy* identyfikator<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *cyfra* identyfikatora

*niecyfrowe*: jedno z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ a b c d e f g h i j k l litera p q r s t u w x y z**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F G H I J K L LITERA O P Q R S T U W X Y Z**

*cyfra*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

Pierwszym znakiem nazwy identyfikatora musi być `nondigit` (to oznacza, że pierwszy znak musi być podkreśleniem lub wielką lub małą literą). ANSI dopuszcza sześć znaczących znaków w nazwie zewnętrznego identyfikatora i 31 dla nazw wewnętrznych (w ramach funkcji). Identyfikatory zewnętrzne (deklarowane w zakresie globalnym lub zadeklarowane za `extern`pomocą klasy magazynu) mogą podlegać dodatkowym ograniczeniom nazewnictwa, ponieważ te identyfikatory muszą być przetwarzane przez inne oprogramowanie, takie jak linki.

**Specyficzne dla firmy Microsoft**

Chociaż ANSI dopuszcza 6 znaków znaczących w zewnętrznych nazwach identyfikatorów i 31 dla nazw wewnętrznych (w ramach funkcji), kompilator języka Microsoft C zezwala na 247 znaków w wewnętrznej lub zewnętrznej nazwie identyfikatora. Jeśli nie ma potrzeby zgodności ze standardem ANSI, można zmodyfikować to ustawienie domyślne na mniejszą lub większą liczbę przy użyciu opcji/H (ograniczaj długość nazw zewnętrznych).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Kompilator języka C traktuje wielkie i małe litery jako odrębne znaki. Ta funkcja o nazwie "czułość wielkości liter" umożliwia tworzenie odrębnych identyfikatorów, które mają takie same pisownia, ale różne przypadki dla jednej lub kilku liter. Na przykład każdy z następujących identyfikatorów jest unikatowy:

```
add
ADD
Add
aDD
```

**Specyficzne dla firmy Microsoft**

Nie wybieraj nazw dla identyfikatorów, które zaczynają się od dwóch znaków podkreślenia lub znaku podkreślenia, po którym następuje Wielka litera. Standard ANSI C umożliwia określenie nazw identyfikatorów rozpoczynających się od tych kombinacji znaków, które mają zostać zarezerwowane do użycia przez kompilator. Identyfikatorów z zakresem plików nie należy również nazywać znakiem podkreślenia i małą literą w postaci dwóch pierwszych liter. Nazwy identyfikatorów, które zaczynają się od tych znaków, również są zastrzeżone. Zgodnie z Konwencją firma Microsoft używa znaku podkreślenia i Wielkiej litery, aby rozpocząć nazwy makr i podwójne podkreślenie dla nazw słów kluczowych specyficznych dla firmy Microsoft. Aby uniknąć konfliktów nazw, zawsze wybieraj nazwy identyfikatorów, które nie rozpoczynają się od jednej lub dwóch znaków podkreślenia lub nazwy rozpoczynające się od znaku podkreślenia, po którym następuje Wielka litera.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Poniżej przedstawiono przykłady prawidłowych identyfikatorów, które są zgodne z ograniczeniami nazewnictwa ANSI lub Microsoft:

```
j
count
temp1
top_of_page
skip12
LastNum
```

**Specyficzne dla firmy Microsoft**

Chociaż identyfikatory w plikach źródłowych uwzględniają wielkość liter domyślnie, symbole w plikach obiektów nie są. Program Microsoft C traktuje identyfikatory w ramach jednostki kompilacji jako z uwzględnieniem wielkości liter.

W konsolidatorze firmy Microsoft jest rozróżniana wielkość liter. Wszystkie identyfikatory należy określić spójnie zgodnie z wielkością liter.

"Źródłowy zestaw znaków" jest zestaw znaków prawnych, które mogą być wyświetlane w plikach źródłowych. W przypadku języka Microsoft C zestaw źródłowy jest standardowym zestawem znaków ASCII. Zbiór znaków źródłowych i zestaw znaków wykonywania zawierają znaki ASCII używane jako sekwencje ucieczki. Zobacz [stałe znakowe](../c-language/c-character-constants.md) , aby uzyskać informacje o zestawie znaków wykonania.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Identyfikator ma wartość "Scope", czyli region programu, w którym jest znany i "powiązanie", które określa, czy ta sama nazwa w innym zakresie odwołuje się do tego samego identyfikatora. Te tematy zostały wyjaśnione w [okresie istnienia, zakresu, widoczności i powiązania](../c-language/lifetime-scope-visibility-and-linkage.md).

## <a name="see-also"></a>Zobacz też

[Elementy języka C](../c-language/elements-of-c.md)
