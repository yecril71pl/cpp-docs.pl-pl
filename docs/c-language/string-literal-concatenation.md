---
title: Łączenie literałów ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- concatenating strings
- strings [C++], concatenating
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0d960a766c14b1e05dab461087669c0d44627d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090085"
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

Aby wymusić nowy wiersz w ciągu literału, wprowadź sekwencję ucieczki nowego wiersza (**\n**) w punkcie w ciągu, w którym ma być złamany następujący wiersz:

```
"Enter a number between 1 and 100\nOr press Return"
```

Ponieważ ciągi mogą rozpoczynać się w dowolnej kolumnie kodu źródłowego, a długie ciągi mogą być kontynuowane w dowolnej kolumnie następnego wiersza, możesz pozycjonować ciągi, aby zwiększyć czytelność kodu źródłowego. W obu przypadkach, reprezentacja danych wyjściowych na ekranie jest nienaruszona. Na przykład:

```
printf_s ( "This is the first half of the string, "
           "this is the second half ") ;
```

Tak długo, jak każda część ciągu jest ujęta w znaki podwójnego cudzysłowu, części są łączone, a wyjście jest pojedynczym ciągiem. Łączenie to zachodzi zgodnie z sekwencją zdarzeń podczas kompilacji, określony przez [fazy tłumaczenia](../preprocessor/phases-of-translation.md).

```
"This is the first half of the string, this is the second half"
```

Wskaźnik ciągu, inicjowany jako dwa różne literały ciągu rozdzielone tylko przez odstępy, jest przechowywany jako pojedynczy ciąg (wskaźniki omówiono w [deklaracje wskaźników](../c-language/pointer-declarations.md)). Jeśli wynik został odwołany w poprawny sposób (jak w następującym przykładzie), to jest on identyczny, jak w poprzednim przykładzie.

```
char *string = "This is the first half of the string, "
               "this is the second half";

printf_s( "%s" , string ) ;
```

Na etapie translacji 6, sekwencje znaków wielobajtowych określone przez dowolne sekwencje sąsiadujących literałów ciągu lub literałów ciągów dwubajtowych, są łączone do pojedynczej sekwencji znaków wielobajtowych. W związku z tym, nie projektuj programów w sposób pozwalający na modyfikację literałów ciągu podczas wykonywania. Standard ANSI C określa, że wynik modyfikacji ciągu jest niezdefiniowany.

## <a name="see-also"></a>Zobacz też

[Literały ciągu języka C](../c-language/c-string-literals.md)