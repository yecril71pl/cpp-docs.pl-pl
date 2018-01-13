---
title: "Długie nazwy plików w pliku reguł programu make | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, long filenames
- long filenames
ms.assetid: 626d56fc-8879-46ba-9c2d-dd386c78cccc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f808faff82e9fcd29040f8d15e6cbaa9e037733
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="long-filenames-in-a-makefile"></a>Długie nazwy plików w pliku reguł programu Make
Ujmij długie nazwy plików w znaki cudzysłowu, w następujący sposób:  
  
```  
all : "VeryLongFileName.exe"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zawartość pliku reguł programu Make](../build/contents-of-a-makefile.md)