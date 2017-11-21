---
title: "Mapowania zmiennych globalnych i stałych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
dev_langs: C++
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 55c388ddddb5fd774afb6c4e84d6a96a4c38bebe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="constant-and-global-variable-mappings"></a>Mapowania zmiennych globalnych i stałych
Te stała zwykłego tekstu, zmiennej globalnej i mapowania standardowy typ są zdefiniowane w tchar —. H i zależą od tego, czy stała `_UNICODE` lub `_MBCS` został zdefiniowany w programie.  
  
### <a name="generic-text-constant-and-global-variable-mappings"></a>Mapowania zwykłego tekstu globalnych i stałych zmiennej  
  
|Zwykłego tekstu — nazwa obiektu|SBCS (_unicode —, _MBCS nie jest zdefiniowana)|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|----------------------------------|--------------------------------------------|--------------------|-----------------------|  
|`_TEOF`|`EOF`|`EOF`|`WEOF`|  
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowania zwykłego tekstu](../c-runtime-library/generic-text-mappings.md)   
 [Mapowanie typu danych](../c-runtime-library/data-type-mappings.md)   
 [Mapowanie procedur](../c-runtime-library/routine-mappings.md)   
 [Przykładowy ogólny Program tekstowy](../c-runtime-library/a-sample-generic-text-program.md)   
 [Mapowania zwykłego tekstu](../c-runtime-library/using-generic-text-mappings.md)