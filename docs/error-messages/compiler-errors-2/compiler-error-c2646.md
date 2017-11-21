---
title: "C2646 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2646
dev_langs: C++
helpviewer_keywords: C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 353f65b4d9702ed82ff92eae63fcedaa6adba227
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2646"></a>C2646 błąd kompilatora
struktury anonimowe lub union globalnie lub zakresie przestrzeni nazw musi być zadeklarowany jako statyczny  
  
 Anonimowe struktura lub związek miała globalnych lub zakresie przestrzeni nazw nie jest jednak zgłoszone `static`.  
  
 Poniższy przykład generuje C2646 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2646.cpp  
// compile with: /c  
union { int i; };   // C2646 not static  
  
// OK  
static union { int j; };  
union U { int i; };  
```