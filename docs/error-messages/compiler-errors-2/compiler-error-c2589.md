---
title: "C2589 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0c75c6c42bcaa60f95e6f7e5214bb28ce72f65f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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