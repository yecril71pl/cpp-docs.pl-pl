---
title: Operator tworzenia ciągów (#)
ms.date: 11/04/2016
f1_keywords:
- '#'
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
ms.openlocfilehash: 4f23eea017197ae1f984e097bb3967c1228fef09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179649"
---
# <a name="stringizing-operator-"></a>Operator tworzenia ciągów (#)

Znak numeru lub operator "tworzenia ciągu" (**#**) konwertuje parametry makr do literałów ciągu bez rozszerzania definicji parametru. Jest on używany tylko z makrami, które przyjmują argumenty. Jeżeli poprzedza on parametr formalny w definicji makra, rzeczywisty argument przekazywany przez wywołanie makra jest ujęty w znaki cudzysłowu i traktowany jako literał ciągu. Literał ciągu następnie zamienia każde wystąpienie kombinacji operatora tworzenia ciągu i parametru formalnego w ramach definicji makra.

> [!NOTE]
> Rozszerzenie Microsoft C (wersje 6.0 i starsze) dla standardu ANSI C, które wcześniej rozszerzało argumenty formalne makra pojawiające się wewnątrz literałów ciągu i stałych ciągu, nie jest już obsługiwane. Kod, który opierał się na tym rozszerzeniu powinien zostać przepisany z użyciem tworzenia ciągu (**#**) — operator.

Odstęp poprzedzający pierwszy token rzeczywistego argumentu i występujący po ostatnim tokenie rzeczywistego argumentu jest ignorowany. Wszelkie odstępy między tokenami w rzeczywistym argumencie są skracane do pojedynczego odstępu w wynikowym literale ciągu. Zatem jeśli komentarz występuje między dwoma tokenami w rzeczywistym argumencie, jest on skracany do jednego odstępu. Wynikowy literał ciągu jest automatycznie łączony z dowolnymi przylegającymi literałami ciągu, od których jest on oddzielony odstępem.

Dalej, jeśli znak zawarty w argumencie zwykle wymaga sekwencji ucieczki w literale ciągu (na przykład znak cudzysłowu (**"**) lub ukośnika odwrotnego (**\\**) znak), niezbędny ukośnik odwrotny ucieczki jest automatycznie wstawiany przed znakiem.

Operator tworzenia ciągu Visual C++ nie działają prawidłowo, gdy jest używany z ciągów, które zawierają sekwencje ucieczki. W takiej sytuacji, kompilator generuje [błąd kompilatora C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md).

## <a name="examples"></a>Przykłady

W poniższym przykładzie pokazano definicję makra, która zawiera operator tworzenia ciągu i główną funkcję, która wywołuje makro:

Takie wywołania będą rozwijane podczas wstępnego przetwarzania, generując poniższy kod:

```cpp
int main() {
   printf_s( "In quotes in the printf function call\n" "\n" );
   printf_s( "\"In quotes when printed to the screen\"\n" "\n" );
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );
}
```

```cpp
// stringizer.cpp
#include <stdio.h>
#define stringer( x ) printf_s( #x "\n" )
int main() {
   stringer( In quotes in the printf function call );
   stringer( "In quotes when printed to the screen" );
   stringer( "This: \"  prints an escaped double quote" );
}
```

```Output
In quotes in the printf function call
"In quotes when printed to the screen"
"This: \"  prints an escaped double quote"
```

W poniższym przykładzie pokazano sposób rozwijania parametru makra:

```cpp
// stringizer_2.cpp
// compile with: /E
#define F abc
#define B def
#define FB(arg) #arg
#define FB1(arg) FB(arg)
FB(F B)
FB1(F B)
```

## <a name="see-also"></a>Zobacz także

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)