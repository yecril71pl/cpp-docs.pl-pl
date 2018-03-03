---
title: "Testowanie znaków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aeea6573b49e3bb093c3eb343ac3c89c27f0466b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="character-testing"></a>Testowanie znaków
**ANSI 4.3.1** zestawów znaków, sprawdzane pod kątem przez `isalnum`, `isalpha`, `iscntrl`, `islower`, `isprint`, i `isupper` funkcji  
  
 Na poniższej liście opisano te funkcje zaimplementowanego przez kompilator C firmy Microsoft.  
  
|Funkcja|Testy|  
|--------------|---------------|  
|`isalnum`|Znaki 0 - 9, A-Z, a-z ASCII 48-57, 65 90, 97 122|  
|`isalpha`|Znaki A-Z, a-z ASCII 65 90, 97 122|  
|`iscntrl`|ASCII 0-31, 127|  
|`islower`|Znaki a-z ASCII 97-122|  
|`isprint`|Znaki A-Z, a-z, 0 - 9 i znaków interpunkcyjnych, miejsce ASCII 32 126|  
|`isupper`|Znaki ASCII 65 90 A-Z|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)