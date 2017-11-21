---
title: Bufor manipulowania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.memory
dev_langs: C++
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1c74c3b9f98f40b87224ae1c12da06ec55207567
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="buffer-manipulation"></a>Manipulowanie buforem
Użyj tych procedur do pracy z obszary pamięci na podstawie po bicie.  
  
### <a name="buffer-manipulation-routines"></a>Manipulowanie buforem procedury  
  
|Procedura|Zastosowanie|  
|-------------|---------|  
|[_memccpy —](../c-runtime-library/reference/memccpy.md)|Kopiowanie znaków z buforu do innego dopóki podany znak lub został skopiowany podana liczba znaków|  
|[memchr, wmemchr —](../c-runtime-library/reference/memchr-wmemchr.md)|Zwraca wskaźnik do pierwszego wystąpienia, w ciągu określonej liczby znaków, z podany znak w buforze|  
|[funkcji memcmp, wmemcmp —](../c-runtime-library/reference/memcmp-wmemcmp.md)|Porównanie określoną liczbę znaków z dwóch buforów|  
|[memcpy, wmemcpy —](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s —, wmemcpy_s —](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Skopiuj określoną liczbę znaków z buforu na inny|  
|[_memicmp —, _memicmp_l —](../c-runtime-library/reference/memicmp-memicmp-l.md)|Porównanie określoną liczbę znaków z dwóch buforów bez uwzględniania wielkości liter|  
|[memmove —, wmemmove —](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s —, wmemmove_s —](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Skopiuj określoną liczbę znaków z buforu na inny|  
|[memset —, wmemset —](../c-runtime-library/reference/memset-wmemset.md)|Użyj danego znaku zainicjować określoną liczbę bajtów w buforze|  
|[_swab —](../c-runtime-library/reference/swab.md)|Wymiana bajtów danych i zapisywania ich w określonej lokalizacji|  
  
 Gdy obszary źródłowe i docelowe nakładają się, tylko `memmove` może skopiować pełną źródła poprawnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)