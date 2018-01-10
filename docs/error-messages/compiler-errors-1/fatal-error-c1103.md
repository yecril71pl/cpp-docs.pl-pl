---
title: "Błąd krytyczny C1103 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1103
dev_langs: C++
helpviewer_keywords: C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f35bcec3b89e8e6c95740d1efb2dbbe98851f1a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1103"></a>Błąd krytyczny C1103
krytyczny błąd importu progid: "komunikat"  
  
 Kompilator wykrył problem Importowanie biblioteki typów.  Na przykład nie można określić biblioteki typów z progid i również określić `no_registry`.  
  
 Aby uzyskać więcej informacji, zobacz [#import — dyrektywa](../../preprocessor/hash-import-directive-cpp.md).  
  
 Poniższy przykład wygeneruje C1103:  
  
```  
// C1103.cpp  
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103  
```