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
ms.openlocfilehash: 139eedf54ab42ddc34b5c049abfcd1c2638c5efc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620080"
---
# <a name="c-operators"></a>Operatory języka C

Operatory języka C stanowią podzestaw [wbudowanych operatorów języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md).

Istnieją trzy typy operatorów. Wyrażenie jednoargumentowe składa się z jednej dołączony do operand operatora jednoargumentowego lub **sizeof** słowa kluczowego, wraz z wyrażeniem. Wyrażenie może być nazwy zmiennej lub wyrażenia rzutowania. Jeśli wyrażenie jest wyrażeniem rzutowania, muszą być ujęte w nawiasy. Wyrażenia binarnego składa się z dwóch argumentów operacji dołączane za pomocą operatora binarnego. Wyrażenie trójargumentowy składa się z trzech argumentów dołączane za pomocą funkcji operator wyrażenia warunkowego.

C obejmuje następujące operatory jednoargumentowe:

|Symbol|Nazwa|
|------------|----------|
|**-** **~** **!**|Operatory negacji i dopełnienia|
|**&#42;** **&**|Operatory pośrednie i adresu|
|**sizeof**|Size — operator|
|**+**|Jednoargumentowy operator plus|
|**++** **--**|Jednoargumentowy inkrementacji i dekrementacji operatorów|

Operatory dwuargumentowe są skojarzone od lewej do prawej. C, oferuje następujące operatory binarne:

|Symbol|Nazwa|
|------------|----------|
|**&#42;** **/** **%**|Operatory multiplikatywne|
|**+** **-**|Operatory addytywne|
|**\<\<** **>>**|Operatory przesunięcia|
|**\<** **>** **\<=** **>=** **==** **!=**|Operatory relacyjne|
|**&** **&#124;** **^**|Operatory bitowe|
|**&&** **&#124;&#124;**|Operatory logiczne|
|**,**|Operator obliczania sekwencyjnego|

Podstawowa — operator (**: >**), obsługiwane przez poprzednie wersje kompilatora C Microsoft 16-bitowych, jest opisana w [podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md).

Operator wyrażenia warunkowego ma niższy priorytet niż wyrażenia binarne i różni się od nich w jest łączność do prawej strony.

Wyrażenia z operatorami także wyrażeń przypisania, które jednoargumentowe lub operatory binarne przypisania. Jednoargumentowe operatory przypisania są przyrost (**++**) i dekrementacji (**--**) operatory; plik binarny operatory przypisania są operator przypisania prostego (**=**) i operatory przypisania złożone. Każdy operator przypisania złożone składa się z innego operatora binarnego operatora przypisania prostego.

## <a name="see-also"></a>Zobacz także

- [Wyrażenia i przydziały](../c-language/expressions-and-assignments.md)
