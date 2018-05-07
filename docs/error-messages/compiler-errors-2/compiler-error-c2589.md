---
title: C2589 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c15589358979f554a9c17114f7d78b05dd83c472
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2589"></a>C2589 błąd kompilatora
"identyfikator": niedozwolony token po prawej stronie "::"  
  
 Jeśli klasy, struktury lub Unii nazwa jest wyświetlana z lewej strony operatora rozpoznawanie zakresów (dwa razy dwukropki), token po prawej stronie musi być klasą, strukturą lub elementu członkowskiego typu union. W przeciwnym razie żadnych identyfikator globalny może występować po prawej stronie.  
  
 Operator rozpoznawania zakresu nie może zostać przeciążony.  
  
 Poniższy przykład generuje C2589:  
  
```  
// C2589.cpp  
void Test(){}  
class A {};  
void operator :: ();   // C2589  
  
int main() {  
   ::Test();  
}  
```