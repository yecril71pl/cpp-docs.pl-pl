---
title: Operatory języka C
ms.date: 06/14/2018
helpviewer_keywords:
- ternary operators
- operators [C]
- symbols, operators
- binary operators
- associativity of operators
- binary data, binary expressions
ms.assetid: 13bc4c8e-2dc9-4b23-9f3a-25064e8777ed
ms.openlocfilehash: 7868073f4932e4b77329e6df4a3de374bcf41ec9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227975"
---
# <a name="c-operators"></a>Operatory języka C

Operatory języka C są podzbiorem [wbudowanych operatorów C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md).

Istnieją trzy typy operatorów. Wyrażenie jednoargumentowe składa się z operatora jednoargumentowego, który jest poprzedzony operandem lub **`sizeof`** słowa kluczowego, po którym następuje wyrażenie. Wyrażenie może być nazwą zmiennej lub wyrażeniem rzutowania. Jeśli wyrażenie jest wyrażeniem rzutowania, musi być ujęte w nawiasy. Wyrażenie binarne składa się z dwóch operandów przyłączonych do operatora binarnego. Wyrażenie Trzyelementowy składa się z trzech operandów przyłączonych do operatora wyrażenia warunkowego.

C zawiera następujące operatory jednoargumentowe:

|Symbol|Nazwa|
|------------|----------|
|**-** **~** **!**|Operatory negacji i uzupełniania|
|**&#42;****&**|Operatory pośrednie i „address-of”|
|**`sizeof`**|Size — operator|
|**+**|Jednoargumentowy operator plus|
|**++** **--**|Operatory przyrostu i zmniejszania jednoargumentowego|

Operatory binarne są kojarzone od lewej do prawej. C zawiera następujące operatory binarne:

|Symbol|Nazwa|
|------------|----------|
|**&#42;** **/****%**|Operatory multiplikatywne|
|**+** **-**|Operatory addytywne|
|**\<\<** **>>**|Operatory przesunięcia|
|**\<** **>****\<=** **>=** **==** **!=**|Operatory relacyjne|
|**&****&#124;****^**|Operatory bitowe|
|**&&****&#124;&#124;**|Operatory logiczne|
|**,**|Operator obliczania sekwencyjnego|

Operator Base (**: >**) obsługiwany przez poprzednie wersje kompilatora 16-bitowego c firmy Microsoft został opisany w artykule [składnia składni języka c](../c-language/c-language-syntax-summary.md).

Operator wyrażenia warunkowego ma niższy priorytet niż wyrażenia binarne i różni się od nich w prawidłowym skojarzeniu.

Wyrażenia z operatorami zawierają również wyrażenia przypisania, które używają jednoargumentowego lub binarnego operatora przypisania. Operatory przypisania jednoargumentowego to operatory przyrostu ( **++** ) i zmniejszania ( **--** ); operatory przypisania binarnego to operator prostego przypisania ( **=** ) i operatory przypisania złożonego. Każdy operator przypisania złożonego jest kombinacją innego operatora binarnego z operatorem przypisania prostego.

## <a name="see-also"></a>Zobacz także

- [Wyrażenia i przydziały](../c-language/expressions-and-assignments.md)
