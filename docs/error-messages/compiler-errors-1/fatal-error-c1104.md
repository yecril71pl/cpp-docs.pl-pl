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
ms.workload: cplusplus
ms.openlocfilehash: ec6f6f7df6187da19b65c399def08be2a021c482
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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