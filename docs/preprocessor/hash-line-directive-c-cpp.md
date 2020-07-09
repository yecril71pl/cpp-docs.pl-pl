---
title: '#line, dyrektywa (C/C++)'
description: 'Opisuje dyrektywę #line, służącą do ustawiania numeru wiersza i nazwy pliku raportowanego przez makra preprocesora.'
ms.date: 07/06/2020
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 7b671cfdf5d5ce43024ac3e038c214396ac8679c
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058623"
---
# <a name="line-directive-cc"></a>#line — dyrektywa (C/C++)

Dyrektywa **#line** nakazuje preprocesorowi ustawić wartości raportowane przez kompilator dla numeru wiersza i nazwy pliku na dany numer wiersza i nazwę pliku.

## <a name="syntax"></a>Składnia

> **`#line`***sekwencja cyfr* ["*filename*"]

## <a name="remarks"></a>Uwagi

Kompilator używa numeru wiersza i opcjonalnie nazwy pliku, aby odwoływać się do błędów znalezionych podczas kompilacji. Zazwyczaj numer wiersza odwołuje się do bieżącego wiersza wejściowego, a nazwa pliku do bieżącego pliku wejściowego. Numer wiersza jest zwiększany po przetworzeniu każdego wiersza.

Wartość *sekwencji cyfr* może być dowolną stałą całkowitą. Zastępowanie makra może być używane na tokenach przetwarzania wstępnego, ale wynik musi być wynikiem odpowiedniej składni. *Nazwa pliku* może być dowolną kombinacją znaków i musi być ujęta w znaki podwójnego cudzysłowu ( `" "` ). Jeśli *Nazwa pliku* zostanie pominięta, poprzednia nazwa pliku pozostaje niezmieniona.

Można zmienić numer linii źródłowej i nazwę pliku, pisząc **`#line`** dyrektywę. **`#line`** Dyrektywa ustawia wartość dla wiersza, który bezpośrednio następuje po dyrektywie w pliku źródłowym. Translator używa numeru wiersza i nazwy pliku do określenia wartości wstępnie zdefiniowanych makr `__FILE__` i `__LINE__` . Możesz użyć tych makr, aby wstawić samoopisowe komunikaty o błędzie do tekstu programu. Aby uzyskać więcej informacji na temat wstępnie zdefiniowanych makr, zobacz [wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md).

`__FILE__`Makro powiększa się do ciągu, którego zawartość jest nazwą pliku, ujętą w podwójne cudzysłowy ( `" "` ).

Jeśli zmienisz numer wiersza i nazwę pliku, kompilator zignoruje poprzednie wartości i będzie kontynuował przetwarzanie z nowymi wartościami. Dyrektywa **#line** jest zwykle używana przez generatory programu. Służy do tego, że komunikaty o błędach odwołują się do oryginalnego pliku źródłowego, a nie do wygenerowanego programu.

## <a name="example"></a>Przykład

Poniższe przykłady ilustrują **`#line`** i `__LINE__` `__FILE__` makra i.

W pierwszym przykładzie numer wiersza ma wartość 10, następnie do 20, a nazwa pliku zostanie zmieniona na *Hello. cpp*.

```cpp
// line_directive.cpp
// Compile by using: cl /W4 /EHsc line_directive.cpp
#include <stdio.h>

int main()
{
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
#line 10
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
#line 20 "hello.cpp"
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
}
```

```Output
This code is on line 7, in file line_directive.cpp
This code is on line 10, in file line_directive.cpp
This code is on line 20, in file hello.cpp
This code is on line 21, in file hello.cpp
```

W tym przykładzie makro `ASSERT` używa wstępnie zdefiniowanych makr `__LINE__` i `__FILE__` do drukowania komunikatu o błędzie o pliku źródłowym, jeśli dana potwierdzenie nie jest prawdziwe.

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Zobacz też

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)
