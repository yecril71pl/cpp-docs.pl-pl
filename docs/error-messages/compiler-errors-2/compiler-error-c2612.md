---
title: "C2612 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2612
dev_langs: C++
helpviewer_keywords: C2612
ms.assetid: 6faacfd6-4455-41a2-808e-0f6799f84d6d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4b7036ae55d381370c7b605b44fc1909f407674
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2612"></a>C2612 błąd kompilatora
końcowe znaki "char" niedozwolony na liście inicjatora podstawowych/elementów członkowskich  
  
 Znak pojawia się po ostatnim podstawowego lub Członkowskiego na liście inicjatora.  
  
 Poniższy przykład generuje C2612:  
  
```  
// C2612.cpp  
class A {  
public:  
   int i;  
   A( int ia ) : i( ia ) + {};   // C2612  
};  
```