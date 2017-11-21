---
title: "C2726 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2726
dev_langs: C++
helpviewer_keywords: C2726
ms.assetid: f0191bb7-c175-450b-bf09-a3213db96d09
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f97067f71927491072f303bc872616640bae3367
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2726"></a>C2726 błąd kompilatora
słowa kluczowego "gcnew" może służyć tylko do utworzenia obiektu z zarządzane lub typu WinRT  
  
 Nie można utworzyć wystąpienia typu natywnego na stercie zbierane pamięci.  
  
 Poniższy przykład generuje C2726 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2726.cpp  
// compile with: /clr  
using namespace System;  
class U {};  
ref class V {};  
value class W {};  
  
int main() {  
   U* pU = gcnew U;    // C2726  
   U* pU2 = new U;   // OK  
   V^ p2 = gcnew V;   // OK  
   W p3;   // OK  
  
}  
```  
