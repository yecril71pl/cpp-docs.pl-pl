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
ms.openlocfilehash: 212f39ee62008b391977aaa91d5c8c4fadfd9730
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336468"
---
# <a name="makefile-preprocessing-operators"></a>Operatory przetwarzania wstępnego pliku reguł programu Make

Wyrażenia przetwarzania wstępnego Makefile mogą używać operatorów, które działają na wartości stałe, kody zakończenia z poleceń, ciągów, makr i ścieżek systemu plików. Aby ocenić wyrażenie, preprocesor najpierw rozszerza makra, a następnie wykonuje polecenia, a następnie wykonuje operacje. Operacje są oceniane w kolejności jawnego grupowania w nawiasach, a następnie w kolejności pierwszeństwa operatora. Wynik jest wartością stałą.

Operator **DEFINED** jest operatorem logicznym, który działa na nazwę makra. Wyrażenie **DEFINED(**_macroname_**)** jest prawdziwe, jeśli *makroskładnik* jest zdefiniowany, nawet jeśli nie ma przypisanej wartości. **ZDEFINIOWANE** w połączeniu z **! JEŻELI** lub **! ELSE IF** jest odpowiednikiem **! IFDEF** lub **! ELSE IFDEF**. Jednak w przeciwieństwie do tych **dyrektyw, DEFINED** może być używany w wyrażeniach złożonych.

Exist **EXIST** Operator jest operator logiczny, który działa na ścieżce systemu plików. **EXIST(**_path_**)** jest true, jeśli *ścieżka* istnieje. Wynik z **EXIST** może służyć w wyrażeniach binarnych. Jeśli *ścieżka* zawiera spacje, należy ją ująć w cudzysłów podwójnych.

Aby porównać dwa ciągi,**==** użyj operatora równości ( ) lub operatora nierówności (**!=**). Ciągi należy ująć w cudzysłów podwójnych.

Stałe całkowite mogą używać operatorów jedno- dla negacji numerycznej**-**(**~**), dopełnienia ( ) i logicznego negacji (**!**).

Wyrażenia można użyć następujących operatorów. Operatory o równym priorytecie są zgrupowane razem, a grupy są wyświetlane w malejącej kolejności pierwszeństwa. Operatory niewymierne kojarzą się z operandem po prawej stronie. Operatory binarne o równym priorytecie kojarzą operandy od lewej do prawej.

|Operator|Opis|
|--------------|-----------------|
|**ZDEFINIOWANE(** *macroname* **)**|Tworzy wartość logiczną dla bieżącego stanu definicji *macroname*.|
|**EXIST(** *ścieżka* **)**|Tworzy wartość logiczną dla istnienia pliku w *ścieżce*.|
|||
|**!**|Jednomyślne logiczne NIE.|
|**~**|Jednoary jest uzupełnieniem.|
|**-**|Negacja jednoznaczna.|
|||
|**&#42;**|Mnożenie.|
|**/**|Dywizji.|
|**%**|Moduł (reszta).|
|||
|**+**|Dodatek.|
|**-**|Odejmowania.|
|||
|**\<\<**|Bitowe przesunięcie w lewo.|
|**>>**|Bitowe przesunięcie w prawo.|
|||
|**\<=**|Mniej niż lub równe.|
|**>=**|Większa lub równa.|
|**\<**|Mniej niż.|
|**>**|Większa niż.|
|||
|**==**|Równości.|
|**!=**|Nierówności.|
|||
|**&**|Bitowe I.|
|**^**|Bitowy XOR.|
|**&#124;**|Bitowy LUB.|
|||
|**&&**|Logiczne I.|
|||
|**&#124;&#124;**|Logiczne LUB.|

> [!NOTE]
> Operator bitowy XOR**^**( ) jest taki sam jak znak **^^** ucieczki i musi być zmieniony (jako) podczas użycia w wyrażeniu.

## <a name="see-also"></a>Zobacz też

- [Wyrażenia w przetwarzaniu wstępnym pliku reguł programu Make](expressions-in-makefile-preprocessing.md)
