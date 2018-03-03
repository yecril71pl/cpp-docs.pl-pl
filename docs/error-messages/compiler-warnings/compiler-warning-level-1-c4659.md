---
title: "Kompilatora (poziom 1) ostrzeżenie C4659 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4659
dev_langs:
- C++
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd974c730a67489d9197b448f02a5042f77159f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4659"></a>Kompilator C4659 ostrzegawcze (poziom 1)
\#pragma "pragma": użycie zastrzeżonego segmentu "segmentu" ma niezdefiniowane zachowanie, użyj #pragma komentarz (konsolidator,...)  
  
 Opcja .drectve był używany do przekazywania opcji do konsolidatora. Zamiast tego użyć pragmy [komentarz](../../preprocessor/comment-c-cpp.md) przekazywania opcji konsolidatora.  
  
```  
// C4659.cpp  
// compile with: /W1 /LD  
#pragma code_seg(".drectve")   // C4659  
```