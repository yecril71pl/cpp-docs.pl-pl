---
title: "Stałe pola ścieżki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
dev_langs: C++
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0adde41ca70fa5fdc457772f6023b02f9550e2ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="path-field-limits"></a>Stałe pola ścieżki
## <a name="syntax"></a>Składnia  
  
```  
#include <stdlib.h>  
```  
  
## <a name="remarks"></a>Uwagi  
 Te stałe zdefiniować maksymalną długość ścieżki i poszczególnych pól w ścieżce.  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_MAX_DIR`|Maksymalna długość składnika katalogu|  
|`_MAX_DRIVE`|Maksymalna długość składnika dysku|  
|`_MAX_EXT`|Maksymalna długość rozszerzenia składnika|  
|`_MAX_FNAME`|Maksymalna długość nazwy pliku składnika|  
|`_MAX_PATH`|Maksymalna długość pełnej ścieżki|  
  
> [!NOTE]
>  C Runtime obsługuje długości maksymalnie 32768 znaków długości, ale zależy od systemu operacyjnego, w szczególności systemu plików, aby obsługiwać te dłuższe ścieżki. Suma pola nie może przekraczać `_MAX_PATH` pełny zapewnienia zgodności z FAT32 systemy plików. [!INCLUDE[win2kfamily](../c-runtime-library/includes/win2kfamily_md.md)], [!INCLUDE[WinXpFamily](../atl/reference/includes/winxpfamily_md.md)], [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], i systemu plików NTFS Vista systemu Windows obsługuje ścieżki do 32768 znaków długości, ale tylko w przypadku korzystania z interfejsów API Unicode. Korzystając z długie nazwy ścieżek, ścieżkę zawierającą znaki prefiksu \\ \\? \ i użyj wersji Unicode funkcje C Runtime.  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe globalne](../c-runtime-library/global-constants.md)