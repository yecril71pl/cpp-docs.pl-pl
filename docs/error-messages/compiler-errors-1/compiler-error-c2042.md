---
title: "C2042 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2042
dev_langs: C++
helpviewer_keywords: C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7907e4407e58e6c05a4c352d78d744d4226153dd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2042"></a>C2042 błąd kompilatora
podpisana niepodpisane słowa kluczowe wykluczają się wzajemnie  
  
 Słowa kluczowe `signed` i `unsigned` są używane w jednej deklaracji.  
  
 Poniższy przykład generuje C2042:  
  
```  
// C2042.cpp  
unsigned signed int i;   // C2042  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2042b.cpp  
// compile with: /c  
unsigned int i;  
signed int ii;  
```