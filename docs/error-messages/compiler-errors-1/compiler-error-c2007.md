---
title: "C2007 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2007
dev_langs: C++
helpviewer_keywords: C2007
ms.assetid: ecd09d99-5036-408b-9e46-bc15488f049e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7b4cb49426125df28793e7d2b7800198a129db3d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2007"></a>C2007 błąd kompilatora
\#Zdefiniuj składni  
  
 Identyfikator nie jest umieszczany po `#define`. Aby rozwiązać problem, należy użyć identyfikatora.  
  
 Poniższy przykład generuje C2007:  
  
```  
// C2007.cpp  
#define   // C2007  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2007b.cpp  
// compile with: /c  
#define true 1  
```