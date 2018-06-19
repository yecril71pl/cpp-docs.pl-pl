---
title: Kategorie regionalne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- LC_MAX
- LC_MIN
- LC_MONETARY
- LC_TIME
- LC_NUMERIC
- LC_COLLATE
- LC_CTYPE
- LC_ALL
dev_langs:
- C++
helpviewer_keywords:
- LC_MIN constant
- LC_MONETARY constant
- LC_CTYPE constant
- locale constants
- LC_MAX constant
- LC_ALL constant
- LC_TIME constant
- LC_NUMERIC constant
- LC_COLLATE constant
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5087fd42a5fd1c104d8587091996e58f78442b1e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392318"
---
# <a name="locale-categories"></a>Kategorie regionalne
## <a name="syntax"></a>Składnia  
  
```  
  
#include <locale.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Kategorie regionalne są stałe manifestu używane przez procedury lokalizacji do określenia, która część informacji o ustawieniach regionalnych programu, który będzie używany. Ustawienia regionalne odwołuje się do lokalizacji (lub Kraj/Region) dla której niektórych aspektów programu można dostosować. Obszary zależnych od ustawień regionalnych to na przykład formatowania dat lub format wyświetlania wartości monetarnych.  
  
|Kategoria ustawień regionalnych|Części programu, których to dotyczy|  
|---------------------|-------------------------------|  
|`LC_ALL`|Wszystkie zachowania ustawień regionalnych (wszystkie kategorie)|  
|`LC_COLLATE`|Zachowanie `strcoll` i `strxfrm` funkcji|  
|`LC_CTYPE`|Zachowanie funkcji obsługi znaków (z wyjątkiem **isdigit —**, `isxdigit`, `mbstowcs`, i `mbtowc`, którego dotyczy to)|  
|`LC_MAX`|Identyczny `LC_TIME`|  
|`LC_MIN`|Identyczny `LC_ALL`|  
|`LC_MONETARY`|Walutowa formatowania informacje zwracane przez `localeconv` — funkcja|  
|`LC_NUMERIC`|Dziesiętnego znak dla procedury sformatowane dane wyjściowe (na przykład `printf`), procedury konwersji danych i niewalutowych formatowania informacje zwracane przez `localeconv` — funkcja|  
|`LC_TIME`|Zachowanie `strftime` — funkcja|  
  
 Zobacz [setlocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md) przykład.  
  
## <a name="see-also"></a>Zobacz też  
 [localeconv —](../c-runtime-library/reference/localeconv.md)   
 [setLocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll — funkcje](../c-runtime-library/strcoll-functions.md)   
 [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)