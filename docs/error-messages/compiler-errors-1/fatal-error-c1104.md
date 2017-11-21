---
title: "Błąd krytyczny C1104 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1104
dev_langs: C++
helpviewer_keywords: C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7a3f7fbff36f998716bc6639ccb718b1699ccf80
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1104"></a>Błąd krytyczny C1104
krytyczny błąd importu libid: "komunikat"  
  
 Kompilator wykrył problem Importowanie biblioteki typów.  Na przykład nie można określić biblioteki typów z identyfikatora libid i również określić `no_registry`.  
  
 Aby uzyskać więcej informacji, zobacz [#import — dyrektywa](../../preprocessor/hash-import-directive-cpp.md).  
  
 Poniższy przykład wygeneruje C1104:  
  
```  
// C1104.cpp  
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104  
```