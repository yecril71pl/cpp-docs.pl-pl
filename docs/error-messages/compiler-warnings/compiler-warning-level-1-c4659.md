---
title: "Kompilatora (poziom 1) ostrzeżenie C4659 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4659
dev_langs: C++
helpviewer_keywords: C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: abaef666a5553969ab1290118b8668c50c2bba3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4659"></a>Kompilator C4659 ostrzegawcze (poziom 1)
\#pragma "pragma": użycie zastrzeżonego segmentu "segmentu" ma niezdefiniowane zachowanie, użyj #pragma komentarz (konsolidator,...)  
  
 Opcja .drectve był używany do przekazywania opcji do konsolidatora. Zamiast tego użyć pragmy [komentarz](../../preprocessor/comment-c-cpp.md) przekazywania opcji konsolidatora.  
  
```  
// C4659.cpp  
// compile with: /W1 /LD  
#pragma code_seg(".drectve")   // C4659  
```