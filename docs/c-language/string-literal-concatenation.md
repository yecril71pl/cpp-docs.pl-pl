---
title: Łączenie literałów ciągu
ms.date: 11/04/2016
helpviewer_keywords:
- concatenating strings
- strings [C++], concatenating
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
ms.openlocfilehash: cdd9a7811635bf43cd76ecbc84d8ab364e7f9dab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157797"
---
# <a name="string-literal-concatenation"></a>Łączenie literałów ciągu

Aby formować literały ciągu, które mają więcej niż jeden wiersz, możesz łączyć ze sobą dwa ciągi. Aby to zrobić, wpisz ukośnik odwrotny, a następnie naciśnij klawisz ENTER. Ukośnik odwrotny powoduje, że kompilator ignoruje następujące znaki nowego wiersza. Na przykład, literał ciągu

```
"Long strings can be bro\
ken into two or more pieces."
```

jest identyczny jak ciąg

```
"Long strings can be broken into two or more pieces."
```

Łączenie ciągów może być używane wszędzie tam, gdzie wcześniej mógł być używany ukośnik odwrotny z następującym po nim znakiem nowego wiersza, aby wprowadzać ciągi dłuższe niż jeden wiersz.

Aby wymusić nowy wiersz w literale ciągu, wprowadź sekwencję ucieczki nowego wiersza (**\n**) w punkcie ciągu, w którym ma zostać przerwany wiersz, w następujący sposób:

```
"Enter a number between 1 and 100\nOr press Return"
```

Ponieważ ciągi mogą rozpoczynać się w dowolnej kolumnie kodu źródłowego, a długie ciągi mogą być kontynuowane w dowolnej kolumnie następnego wiersza, możesz pozycjonować ciągi, aby zwiększyć czytelność kodu źródłowego. W obu przypadkach, reprezentacja danych wyjściowych na ekranie jest nienaruszona. Przykład:

```
printf_s ( "This is the first half of the string, "
           "this is the second half ") ;
```

Tak długo, jak każda część ciągu jest ujęta w znaki podwójnego cudzysłowu, części są łączone, a wyjście jest pojedynczym ciągiem. Łączenie odbywa się zgodnie z sekwencją zdarzeń podczas kompilacji określonej przez [etapy tłumaczenia](../preprocessor/phases-of-translation.md).

```
"This is the first half of the string, this is the second half"
```

Wskaźnik ciągu, zainicjowany jako dwa odrębne literały ciągu oddzielone tylko przez biały znak, jest przechowywany jako pojedynczy ciąg (wskaźniki są omówione w [deklaracjach wskaźników](../c-language/pointer-declarations.md)). Jeśli wynik został odwołany w poprawny sposób (jak w następującym przykładzie), to jest on identyczny, jak w poprzednim przykładzie.

```
char *string = "This is the first half of the string, "
               "this is the second half";

printf_s( "%s" , string ) ;
```

Na etapie translacji 6, sekwencje znaków wielobajtowych określone przez dowolne sekwencje sąsiadujących literałów ciągu lub literałów ciągów dwubajtowych, są łączone do pojedynczej sekwencji znaków wielobajtowych. W związku z tym, nie projektuj programów w sposób pozwalający na modyfikację literałów ciągu podczas wykonywania. Standard ANSI C określa, że wynik modyfikacji ciągu jest niezdefiniowany.

## <a name="see-also"></a>Zobacz też

[Literały ciągu języka C](../c-language/c-string-literals.md)
