---
title: C2688 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2688
dev_langs:
- C++
helpviewer_keywords:
- C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd2ebb16acfbc5c7d540e877baab909a950c7f55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236017"
---
# <a name="compiler-error-c2688"></a>C2688 błąd kompilatora
"C2::fgrv": kowariantne wyniki zwracane z wielokrontym lub wirtualnym dziedziczeniem nie są obsługiwane przez funkcję varargs  
  
 Kowariantne typy zwracane nie są obsługiwane w programie Visual C++, gdy funkcja zawiera zmiennych argumentów.  
  
 Aby rozwiązać ten problem, zdefiniuj funkcji tak, aby nie używać zmiennych argumentów lub taka sama dla wszystkich funkcji wirtualnych wprowadzić wartości zwracanych.  
  
 Poniższy przykład generuje C2688:  
  
```  
// C2688.cpp  
struct G1 {};  
struct G2 {};  
struct G3 : G1, G2 {};  
struct G4 {};  
struct G5 {};  
struct G6 : G4, G5 {};  
struct G7 : G3, G6 {};  
  
struct C1 {  
   virtual G4& fgrv(int,...);  
};  
  
struct C2 : C1 {  
   virtual G7& fgrv(int,...);   // C2688, does not return G4&  
};  
```