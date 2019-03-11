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
ms.openlocfilehash: 44c7a280ebffd0073f1dfb3a0a3cbdbd2efee0fb
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745367"
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

## <a name="see-also"></a>Zobacz także

[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
