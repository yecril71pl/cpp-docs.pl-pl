---
title: "C2803 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2472c0e1182ad11f5ea95e3411649e6214b110ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2803"></a>C2803 błąd kompilatora
"operator operator" musi mieć co najmniej jeden formalny parametr typu klasy  
  
 Przeciążony operator nie ma parametru typu klasy.  
  
 Należy przekazać co najmniej jeden parametr przez odwołanie (nie używa wskaźników, lecz przywołuje) lub wartość, aby można było zapisać "< b" (typ klasy A i b).  
  
 Jeśli oba parametry są wskaźnikami będzie czysty porównania wskaźnika adresów i nie będzie używać konwersji zdefiniowanej przez użytkownika.  
  
 Poniższy przykład generuje C2803:  
  
```  
// C2803.cpp  
// compile with: /c  
class A{};  
bool operator< (const A *left, const A *right);   // C2803  
// try the following line instead  
// bool operator< (const A& left, const A& right);  
```