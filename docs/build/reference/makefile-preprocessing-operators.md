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
ms.openlocfilehash: 2276f6a3c28c6f2fac509ef0e4bc14cce9932582
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170466"
---
# <a name="makefile-preprocessing-operators"></a>Operatory przetwarzania wstępnego pliku reguł programu Make

Wyrażenia przetwarzania wstępnego pliku reguł programu make mogą używać operatorów, które działają na wartościach stałych, kody wyjścia z poleceń, ciągów, makr i ścieżek systemu plików. Aby oszacować wyrażenie, preprocesor najpierw rozszerza makra, a następnie wykonuje polecenia, a następnie wykonuje operacje. Operacje są oceniane w kolejności jawnej grupowania w nawiasach, a następnie w kolejności pierwszeństwa operatorów. Wynik jest wartością stałą.

**Zdefiniowany** operator jest operatorem logicznym, który działa w nazwie makra. Wyrażenie **zdefiniowane (** _Macroname_ **)** ma wartość true, jeśli określono wartość *Macroname* , nawet jeśli nie ma przypisanej wartości. **Zdefiniowane** w połączeniu z **! IF** lub **! ELSE IF** jest równoważne **! IFDEF** lub **! ELSE IFDEF**. Jednak w przeciwieństwie do tych dyrektyw, **zdefiniowane** można używać w wyrażeniach złożonych.

Operator **exist** jest operatorem logicznym, który działa na ścieżce systemu plików. **Istnieje (** _ścieżka_ **)** ma wartość true, jeśli *ścieżka* istnieje. Wynik z **istnieje** może być używany w wyrażeniach binarnych. Jeśli *ścieżka* zawiera spacje, ujmij ją w znaki podwójnego cudzysłowu.

Aby porównać dwa ciągi, użyj operatora równości ( **==** ) lub operatora nierówności ( **! =** ). Ciągi ujęte w znaki podwójnego cudzysłowu.

Stałe całkowite mogą używać jednoargumentowych operatorów dla liczbowych negacji ( **-** ), jednego uzupełnienia ( **~** ) i logicznego negacji ( **!** ).

Wyrażenia mogą używać następujących operatorów. Operatory równego pierwszeństwa są grupowane razem, a grupy są wyświetlane w kolejności malejącej pierwszeństwa. Operatory jednoargumentowe są kojarzone z argumentem operacji po prawej stronie. Operatory binarne o równych priorytetach kojarzą operandy od lewej do prawej.

|Operator|Opis|
|--------------|-----------------|
|**Zdefiniowane (** *Macroname* **)**|Tworzy wartość logiczną dla bieżącego stanu definicji *Macroname*.|
|**Istnieje (** *ścieżka* **)**|Tworzy wartość logiczną dla istnienia pliku w *ścieżce*.|
|||
|**!**|Logiczne jednoargumentowe NOT.|
|**~**|Jednoargumentowy uzupełnienie jednego.|
|**-**|Jednoargumentowa Negacja.|
|||
|**&#42;**|Mnożenia.|
|**/**|Dzielenie.|
|**%**|Moduł (reszta).|
|||
|**+**|Dodatek.|
|**-**|Odejmowanie.|
|||
|**\<\<**|Przesunięcie bitowe w lewo.|
|**>>**|Przesunięcie bitowe w prawo.|
|||
|**\<=**|Mniejsze niż lub równe.|
|**>=**|Większe niż lub równe.|
|**\<**|Mniejsze niż.|
|**>**|Większe niż.|
|||
|**==**|Kryteri.|
|**!=**|Nierówności.|
|||
|**&**|Operatora bitowego AND.|
|**^**|Bitowe XOR.|
|**&#124;**|Bitowe OR.|
|||
|**&&**|Koniunkcja logiczna i.|
|||
|**&#124;&#124;**|Logiczne OR.|

> [!NOTE]
> Bitowy operator XOR ( **^** ) jest taki sam jak znak ucieczki i musi mieć wartość ucieczki (jako **^^** ), gdy jest używany w wyrażeniu.

## <a name="see-also"></a>Zobacz też

- [Wyrażenia w przetwarzaniu wstępnym pliku reguł programu Make](expressions-in-makefile-preprocessing.md)
