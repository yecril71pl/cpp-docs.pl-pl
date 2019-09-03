---
title: 'Operator wklejania tokenu (# #)'
ms.date: 08/29/2019
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: 4bf1b8c8f56ab9375503c9e8fb6a906706fc70bb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218104"
---
# <a name="token-pasting-operator-"></a>Operator wklejania tokenu (# #)

Operator podwójnego numeru lub wklejanie *tokenów* ( **##** ), który jest czasami nazywany operatorem *scalania* lub *łączenia* , jest używany zarówno w makrach jak i podobnej do funkcji. Zezwala na przyłączenie oddzielnych tokenów do jednego tokenu i dlatego nie może być pierwszym lub ostatnim tokenem w definicji makra.

Jeśli parametr formalny w definicji makra jest poprzedzany lub następuje operator wklejania tokenu, parametr formalny jest natychmiast zastępowany przez nierozwinięty argument rzeczywisty. Nie wykonano rozwinięcia makra dla argumentu przed zastąpieniem.

Następnie każde wystąpienie operatora wklejania tokenu w *ciągu tokenu* jest usuwane, a tokeny poprzedzające i poniższe są łączone. Token wynikający musi być prawidłowym tokenem. Jeśli tak jest, token jest skanowany pod kątem możliwego zastąpienia, jeśli reprezentuje nazwę makra. Identyfikator reprezentuje nazwę, za pomocą której będą znane tokeny połączone w programie przed zastąpieniem. Każdy token reprezentuje token zdefiniowany w innym miejscu w programie lub w wierszu polecenia kompilatora. Spacja poprzedzająca lub poniżej operatora jest opcjonalna.

Ten przykład ilustruje użycie operatorów tworzenia ciągu i wklejania tokenu w temacie określanie danych wyjściowych programu:

```cpp
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;
```

Jeśli makro jest wywoływane z argumentem liczbowym podobnym do

```cpp
paster( 9 );
```

makro daje

```cpp
printf_s( "token" "9" " = %d", token9 );
```

który zostanie

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

## <a name="see-also"></a>Zobacz także

[Operatory preprocesora](../preprocessor/preprocessor-operators.md)
