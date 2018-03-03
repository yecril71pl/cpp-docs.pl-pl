---
title: "Stałe stercie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e2e1a15b371aa4f2997d453e2543123b279ac0df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 [_heapchk —](../c-runtime-library/reference/heapchk.md)   
 [_heapset —](../c-runtime-library/heapset.md)   
 [_heapwalk —](../c-runtime-library/reference/heapwalk.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)