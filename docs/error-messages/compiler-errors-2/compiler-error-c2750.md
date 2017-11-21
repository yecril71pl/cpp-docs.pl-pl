---
title: "C2750 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2750
dev_langs: C++
helpviewer_keywords: C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fbe3ee423183bb841e3e6777db94e4645b94355d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2750"></a>C2750 błąd kompilatora
'type': nie można użyć "new" na typ referencyjny; Zamiast tego użyj słowa kluczowego "gcnew"  
  
 Aby utworzyć wystąpienia typu CLR, co powoduje, że wystąpienie na stercie zbierane pamięci, należy użyć [gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
 Poniższy przykład generuje C2750:  
  
```  
// C2750.cpp  
// compile with: /clr  
ref struct Y1 {};  
  
int main() {  
   Y1 ^ x = new Y1;   // C2750  
  
   // try the following line instead  
   Y1 ^ x2 = gcnew Y1;  
}  
```