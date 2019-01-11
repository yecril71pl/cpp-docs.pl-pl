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
ms.openlocfilehash: b8783a5826376a65cb71444e2d64c61b6938eab8
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220221"
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
