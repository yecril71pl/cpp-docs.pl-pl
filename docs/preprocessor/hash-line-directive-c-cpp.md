---
title: '#wiersz — dyrektywa (C/C++)'
ms.date: 10/18/2017
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: ad0fe1514e89b861bab046652b1768862cc8045b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383779"
---
# <a name="line-directive-cc"></a>#line — dyrektywa (C/C++)

**#Line** dyrektywy nakazuje preprocesorowi Zmień kompilatora wewnętrznie przechowywany numer wiersza i nazwę pliku na podany numer wiersza i nazwę pliku.

## <a name="syntax"></a>Składnia

> **#line** *sekwencję cyfr* ["*filename*"]

## <a name="remarks"></a>Uwagi

Kompilator używa numeru wiersza i opcjonalnie nazwy pliku, aby odwoływać się do błędów znalezionych podczas kompilacji. Zazwyczaj numer wiersza odwołuje się do bieżącego wiersza wejściowego, a nazwa pliku do bieżącego pliku wejściowego. Numer wiersza jest zwiększany po przetworzeniu każdego wiersza.

*Sekwencję cyfr* wartość może być dowolną stałą całkowitą. Zamiana makro może zostać wykonana na tokenach przetwarzania wstępnego, ale wynik musi zostać oszacowany według poprawnej składni. *Filename* może być dowolną kombinacją znaków i musi być ujęte w podwójny cudzysłów (**""**). Jeśli *filename* jest pominięty, nazwa_pliku poprzedniego pozostaje bez zmian.

Możesz zmienić numer wiersza źródła i nazwę pliku, pisząc **#line** dyrektywy. Translator używa numeru wiersza i nazwę pliku można określić wartości predefiniowanych makr `__FILE__` i `__LINE__`. Możesz użyć tych makr, aby wstawić samoopisowe komunikaty o błędzie do tekstu programu. Aby uzyskać więcej informacji na temat wstępnie zdefiniowanych makr, zobacz [wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md).

`__FILE__` Makro rozszerzy się na ciąg, którego zawartością jest nazwa pliku ujęta w znaki podwójnego cudzysłowu (**""**).

Jeśli zmienisz numer wiersza i nazwę pliku, kompilator zignoruje poprzednie wartości i będzie kontynuował przetwarzanie z nowymi wartościami. **#Line** — dyrektywa jest zwykle używana przez generatory programu, aby spowodować, że komunikaty o błędach do odwoływania się do oryginalnego pliku źródłowego zamiast wygenerowanego programu.

Poniższe przykłady ilustrują **#line** i `__LINE__` i `__FILE__` makra.

W niniejszych wewnętrznie przechowywany numer wiersza został ustawiony na 151, a nazwa pliku jest zmieniana na copy.c.

```cpp
#line 151 "copy.c"
```

W tym przykładzie, makro `ASSERT` używa wstępnie zdefiniowane makra `__LINE__` i `__FILE__` Aby wydrukować komunikat o błędzie dotyczący pliku źródłowego, jeśli dany potwierdzenie nie zostanie spełniony.

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)