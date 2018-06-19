---
title: C2803 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51cf2a8b38a86fcd97ab693b3853fe25527a0bb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236226"
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