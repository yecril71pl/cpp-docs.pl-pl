---
title: Heap — Stałe
ms.date: 11/04/2016
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
ms.openlocfilehash: 9419ae53cd04812f45f5feeee73fa0f89c408a0c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522301"
---
# <a name="heap-constants"></a>Heap — Stałe

## <a name="syntax"></a>Składnia

```

#include <malloc.h>
```

## <a name="remarks"></a>Uwagi

Te stałe nadać wartość zwracaną, wskazujący stan sterty.

|Stała|Znaczenie|
|--------------|-------------|
|`_HEAPBADBEGIN`|Informacje o nagłówku początkowy nie został znaleziony lub jest ono nieprawidłowe.|
|`_HEAPBADNODE`|Znaleziono nieprawidłowy węzeł lub uszkodzenia sterty.|
|`_HEAPBADPTR`|**_pentry** pole **_heapinfo —** struktury nie zawiera prawidłowego wskaźnika do sterty (`_heapwalk` procedury tylko).|
|`_HEAPEMPTY`|Nie zainicjowano stosu.|
|`_HEAPEND`|Koniec sterty osiągnięty został pomyślnie (`_heapwalk` procedury tylko).|
|`_HEAPOK`|Sterta to spójne (`_heapset` i `_heapchk` procedury tylko). Brak błędów do tej pory; **_Heapinfo —** struktura zawiera informacje o następnej pozycji (`_heapwalk` procedury tylko).|

## <a name="see-also"></a>Zobacz też

[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)