---
title: Operator tworzenia ciągów (#)
ms.date: 08/29/2019
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
ms.openlocfilehash: 5a1b43198e59bc1e69cdf1b56db56be75719fe46
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216548"
---
# <a name="stringizing-operator-"></a>Operator tworzenia ciągów (#)

Operator Number-Sign lub "tworzenia ciągu" ( **#** ) konwertuje parametry makr na literały ciągu bez rozszerzania definicji parametru. Jest ona używana tylko z makrami, które przyjmują argumenty. Jeżeli poprzedza on parametr formalny w definicji makra, rzeczywisty argument przekazywany przez wywołanie makra jest ujęty w znaki cudzysłowu i traktowany jako literał ciągu. Literał ciągu następnie zamienia każde wystąpienie kombinacji operatora tworzenia ciągu i parametru formalnego w ramach definicji makra.

> [!NOTE]
> Rozszerzenie Microsoft C (wersje 6.0 i starsze) dla standardu ANSI C, które wcześniej rozszerzało argumenty formalne makra pojawiające się wewnątrz literałów ciągu i stałych ciągu, nie jest już obsługiwane. Kod, który opiera się na tym rozszerzeniu, należy napisać ponownie przy użyciu **#** operatora tworzenia ciągu ().

Biały znak poprzedzający pierwszy token i następujący po ostatnim tokenie rzeczywistego argumentu jest ignorowany. Wszelkie odstępy między tokenami w rzeczywistym argumencie są skracane do pojedynczego odstępu w wynikowym literale ciągu. Tak więc, jeśli komentarz występuje między dwoma tokenami w rzeczywistym argumencie, zostaje zredukowany do pojedynczego odstępu. Ciąg literału ciągu jest automatycznie łączony z dowolnymi sąsiednimi literałami ciągów, które są rozdzielone tylko odstępem.

Ponadto, jeśli znak zawarty w argumencie zazwyczaj wymaga sekwencji ucieczki, gdy jest używany w literale ciągu, na przykład znak cudzysłowu (`"`) lub ukośnik odwrotny (`\`), niezbędny ukośnik odwrotny jest automatycznie wstawiono przed znakiem.

Operator Microsoft C++ tworzenia ciągu nie działa prawidłowo, gdy jest używany z ciągami, które zawierają sekwencje ucieczki. W tej sytuacji kompilator generuje [błąd kompilatora C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md).

## <a name="examples"></a>Przykłady

W poniższym przykładzie przedstawiono definicję makra zawierającą operator tworzenia ciągu oraz główną funkcję, która wywołuje makro:

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

`stringer` Makra są rozszerzane podczas przetwarzania wstępnego, generując następujący kod:

```cpp
int main() {
   printf_s( "In quotes in the printf function call" "\n" );
   printf_s( "\"In quotes when printed to the screen\"" "\n" );
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );
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
