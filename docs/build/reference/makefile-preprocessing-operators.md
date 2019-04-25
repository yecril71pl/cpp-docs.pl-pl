---
title: Operatory przetwarzania wstępnego pliku reguł programu Make
ms.date: 06/14/2018
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
ms.openlocfilehash: 4101c2fe30bcba44e9b69ed4d6d022845e6e8904
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321582"
---
# <a name="makefile-preprocessing-operators"></a>Operatory przetwarzania wstępnego pliku reguł programu Make

Pliku reguł programu make wstępnego przetwarzania wyrażenia można użyć operatorów, które działają na stałe wartości, kody wyjścia z poleceń, ciągi, makr i ścieżki systemu plików. Można obliczyć wyrażenia, preprocesor najpierw rozszerza makra i następnie wykonuje polecenia, a następnie wykonuje operacje. Operacje są obliczane w kolejności jawne grupowania w nawiasach, a następnie zgodnie z kolejnością pierwszeństwo operatorów. Wynik jest wartością stałą.

**Zdefiniowane** operator jest operator logiczny, który działa na nazwę makra. Wyrażenie **zdefiniowane (**_makra_**)** ma wartość true Jeśli *makra* jest zdefiniowany, nawet jeśli nie ma przypisaną wartość. **ZDEFINIOWANE** w połączeniu z **! Jeśli** lub **! Jeśli nie** jest odpowiednikiem **! IFDEF** lub **! ELSE IFDEF**. Jednak w przeciwieństwie do tych dyrektyw **zdefiniowane** mogą być używane w złożonych wyrażeń.

**ISTNIEJE** operator jest operator logiczny, który działa w ścieżce systemu plików. **ISTNIEJE (**_ścieżki_**)** ma wartość true Jeśli *ścieżki* istnieje. Wynik **ISTNIEJE** mogą być używane w wyrażenia binarnego. Jeśli *ścieżki* zawiera spacje, należy ją ująć w znaki podwójnego cudzysłowu.

Aby porównać dwa ciągi, należy użyć równości (**==**) operatora i nierówności (**! =**) — operator. Ciągi należy ująć w znaki podwójnego cudzysłowu.

Stałe całkowite można użyć operatorów jednoargumentowych dla wartości liczbowych negacji (**-**), jednego użytkownika uzupełniają (**~**), a logiczny negacji (**!**).

Wyrażenia można używać następujących operatorów. Operatory równy priorytet są zgrupowane razem i grup są wymienione w kolejności malejącej. Operatory jednoargumentowe skojarzyć z argument operacji po prawej stronie. Operatory dwuargumentowe równe pierwszeństwo skojarzyć argumentów od lewej do prawej.

|Operator|Opis|
|--------------|-----------------|
|**ZDEFINIOWANE (** *makra* **)**|Tworzy wartość logiczną, aby uzyskać bieżący stan definicji *makra*.|
|**ISTNIEJE (** *ścieżki* **)**|Tworzy wartość logiczną, istnieje w pliku, *ścieżki*.|
|||
|**\!**|Jednoargumentowy logiczne NOT.|
|**~**|Jednoargumentowy jednostkowego dopełnienia.|
|**-**|Negacja Jednoargumentowa.|
|||
|**&#42;**|Mnożenia.|
|**/**|Dzielenie.|
|**%**|Moduł (resztę).|
|||
|**+**|Dodatek.|
|**-**|Odejmowanie.|
|||
|**\<\<**|Operatory przesunięcia w lewo.|
|**>>**|Bitowe przesunięcia w prawo.|
|||
|**\<=**|Mniejsze niż lub równe.|
|**>=**|Większe lub równe.|
|**\<**|Mniejsze niż.|
|**>**|Większe niż.|
|||
|**==**|Równości.|
|**\!=**|Nierówności.|
|||
|**&**|Operatora bitowego AND.|
|**^**|Bitowe XOR.|
|**&#124;**|Bitowe OR.|
|||
|**&&**|Operatora logicznego AND.|
|||
|**&#124;&#124;**|Logiczne OR.|

> [!NOTE]
> Bitowy operator XOR (**^**) jest taka sama jak znak ucieczki. Ponadto należy użyć znaków ucieczki (jako **^^**) gdy jest używany w wyrażeniu.

## <a name="see-also"></a>Zobacz także

- [Wyrażenia w przetwarzaniu wstępnym pliku reguł programu Make](expressions-in-makefile-preprocessing.md)