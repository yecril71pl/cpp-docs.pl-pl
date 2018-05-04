---
title: Stałe stercie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25118792500d679d243f55e5d87e62a4994eaa0f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="heap-constants"></a>Heap — Stałe
## <a name="syntax"></a>Składnia  
  
```  
  
#include <malloc.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Te stałe nadaj wartość zwrotną, wskazujący stan sterty.  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_HEAPBADBEGIN`|Informacje o nagłówku początkowy nie został znaleziony lub jest nieprawidłowy.|  
|`_HEAPBADNODE`|Znaleziono nieprawidłowy węzeł lub sterty jest uszkodzony.|  
|`_HEAPBADPTR`|**_pentry** pole **_heapinfo —** struktura nie zawiera prawidłowego wskaźnika do stosu (`_heapwalk` procedury tylko).|  
|`_HEAPEMPTY`|Stos nie został zainicjowany.|  
|`_HEAPEND`|Osiągnięto koniec stosu pomyślnie (`_heapwalk` procedury tylko).|  
|`_HEAPOK`|Stos jest spójna (`_heapset` i `_heapchk` procedury tylko). Do tej pory; bez błędów **_Heapinfo —** struktura zawiera informacje o następnej pozycji (`_heapwalk` procedury tylko).|  
  
## <a name="see-also"></a>Zobacz też  
 [_heapchk](../c-runtime-library/reference/heapchk.md)   
 [_heapset —](../c-runtime-library/heapset.md)   
 [_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)