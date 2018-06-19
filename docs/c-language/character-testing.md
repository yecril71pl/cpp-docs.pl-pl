---
title: Testowanie znaków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdf65de941486cb8256ba8e30a3f186d3e3702d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381697"
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