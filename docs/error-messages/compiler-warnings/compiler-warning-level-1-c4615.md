---
title: "Kompilatora (poziom 1) ostrzeżenie C4615 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4615
dev_langs: C++
helpviewer_keywords: C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0541ea09fedf3c716bf970531735eafaecc048f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4615"></a>Kompilator C4615 ostrzegawcze (poziom 1)
\#warning elementu pragma: Nieznany typ ostrzeżenia użytkownika  
  
 Nieprawidłowy specyfikator ostrzeżenie została użyta z **pragma** [ostrzeżenie](../../preprocessor/warning.md). Aby rozwiązać problem, należy użyć Nieprawidłowy specyfikator ostrzeżenie.  
  
 Poniższy przykład generuje C4615:  
  
```  
// C4615.cpp  
// compile with: /W1 /LD  
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier  
  
// use the code below to resolve the error  
// #pragma warning(default : 4401)  
```