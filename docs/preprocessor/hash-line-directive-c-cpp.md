---
title: '#line, dyrektywa (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 35bee779ebf059c20d4a46e27b5ad4cbfb3ce5f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220225"
---
# <a name="line-directive-cc"></a>#line — dyrektywa (CC++/)

Dyrektywa **#line** nakazuje preprocesorowi zmienić wewnętrznie przechowywane w kompilatorze numer wiersza i nazwę pliku na dany numer wiersza i nazwę pliku.

## <a name="syntax"></a>Składnia

> **#line** *sekwencja cyfr* ["*filename*"]

## <a name="remarks"></a>Uwagi

Kompilator używa numeru wiersza i opcjonalnie nazwy pliku, aby odwoływać się do błędów znalezionych podczas kompilacji. Zazwyczaj numer wiersza odwołuje się do bieżącego wiersza wejściowego, a nazwa pliku do bieżącego pliku wejściowego. Numer wiersza jest zwiększany po przetworzeniu każdego wiersza.

Wartość *sekwencji cyfr* może być dowolną stałą całkowitą. Zamiana makro może zostać wykonana na tokenach przetwarzania wstępnego, ale wynik musi zostać oszacowany według poprawnej składni. *Nazwa pliku* może być dowolną kombinacją znaków i musi być ujęta w znaki podwójnego`" "`cudzysłowu (). Jeśli *Nazwa pliku* zostanie pominięta, poprzednia nazwa pliku pozostaje niezmieniona.

Możesz zmienić numer wiersza źródłowego i nazwę pliku, pisząc **#line** dyrektywę. Translator używa numeru wiersza i nazwy pliku do określenia wartości wstępnie zdefiniowanych makr `__FILE__` i. `__LINE__` Możesz użyć tych makr, aby wstawić samoopisowe komunikaty o błędzie do tekstu programu. Aby uzyskać więcej informacji na temat wstępnie zdefiniowanych makr, zobacz [wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md).

Makro powiększa się do ciągu, którego zawartość jest nazwą pliku, ujętą w podwójne cudzysłowy (`" "`). `__FILE__`

Jeśli zmienisz numer wiersza i nazwę pliku, kompilator zignoruje poprzednie wartości i będzie kontynuował przetwarzanie z nowymi wartościami. Dyrektywa **#line** jest zwykle używana przez generatory programu, aby komunikaty o błędach odwołują się do oryginalnego pliku źródłowego, a nie do wygenerowanego programu.

Poniższe przykłady ilustrują **#line** i `__LINE__` makra i `__FILE__` .

W tej instrukcji wewnętrznie przechowywany numer wiersza jest ustawiony na 151, a nazwa pliku jest zmieniana na Copy. c.

```C
#line 151 "copy.c"
```

W tym przykładzie makro `ASSERT` używa wstępnie zdefiniowanych makr `__LINE__` i `__FILE__` do drukowania komunikatu o błędzie o pliku źródłowym, jeśli dana potwierdzenie nie jest prawdziwe.

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)
