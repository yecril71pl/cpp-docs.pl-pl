---
title: "Stałe uprawnień pliku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _S_IWRITE
- _S_IREAD
dev_langs: C++
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aa42ebf645c737ffe2f5db9647a3ba3912669b27
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="file-permission-constants"></a>Stałe uprawnień pliku
## <a name="syntax"></a>Składnia  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Jedną z tych stałych jest wymagany, gdy `_O_CREAT` (`_open`, `_sopen`) został określony.  
  
 `pmode` Argument określa ustawienia uprawnień pliku w następujący sposób.  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_S_IREAD`|Odczytywanie dozwolone|  
|`_S_IWRITE`|Zapisywanie dozwolone|  
|`_S_IREAD` &#124; `_S_IWRITE`|Odczytywanie i zapisywanie dozwolone|  
  
 Gdy jest używany jako `pmode` argument `_umask`, stała manifestu ustawia ustawienie uprawnienia w następujący sposób.  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_S_IREAD`|Niedozwolony zapis (plik jest tylko do odczytu)|  
|`_S_IWRITE`|Niedozwolone odczytu (plik jest tylko do zapisu)|  
|`_S_IREAD` &#124; `_S_IWRITE`|Zapisywanie ani odczytywanie dozwolone|  
  
## <a name="see-also"></a>Zobacz też  
 [_otwórz, _wopen —](../c-runtime-library/reference/open-wopen.md)   
 [_sopen —, _wsopen —](../c-runtime-library/reference/sopen-wsopen.md)   
 [_umask —](../c-runtime-library/reference/umask.md)   
 [Standardowe typy](../c-runtime-library/standard-types.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)