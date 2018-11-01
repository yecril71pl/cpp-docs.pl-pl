---
title: Operator wklejania tokenu (##)
ms.date: 11/04/2016
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: c013d6a4ce34372e2f195876166e299f62d85d3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605949"
---
# <a name="token-pasting-operator-"></a>Operator wklejania tokenu (##)

Znak numeru double lub "wklejanie tokenów" — operator (**##**), jest czasami nazywane "scalania" operator jest używany w makrach obiektopodobne i funkcyjne. On pozwala oddzielne tokeny mają zostać połączone w pojedynczy token i dlatego nie może być pierwszy lub ostatni token w definicji makra.

Jeśli parametr formalny w definicji makra jest przed lub po operator wklejania tokenu, parametr formalny zastępuje rzeczywisty argument nierozwiniętego natychmiast. Argument przed zastępczy nie jest przeprowadzane rozwinięciu makra.

Następnie w każdym wystąpieniu operator wklejania tokenu w *ciąg tokenu* zostanie usunięty, i są łączone tokenów poprzedzające i następujące go. Wynikowy token musi być prawidłowym tokenem. Jeśli tak jest, token jest skanowany w poszukiwaniu możliwych zastąpienie Jeśli termin reprezentuje nazwę makra. Identyfikator reprezentuje nazwę, za pomocą którego będzie znana połączonych tokenów w programie przed zastępczy. Każdy token reprezentuje token, który został zdefiniowany w innym miejscu, w ramach programu lub w wierszu polecenia kompilatora. Biały znak poprzedzające lub następujące operator jest opcjonalne.

Ten przykład ilustruje użycie oba operatory tworzenia ciągu i wklejania tokenu podczas określania danych wyjściowych programu:

```cpp
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;
```

Jeśli makro jest wywoływana z argumentem liczbowym, takich jak

```cpp
paster( 9 );
```

makro daje

```cpp
printf_s( "token" "9" " = %d", token9 );
```

które stają się

```cpp
printf_s( "token9 = %d", token9 );
```

## <a name="example"></a>Przykład

```cpp
// preprocessor_token_pasting.cpp
#include <stdio.h>
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;

int main()
{
   paster(9);
}
```

```Output
token9 = 9
```

## <a name="see-also"></a>Zobacz też

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)