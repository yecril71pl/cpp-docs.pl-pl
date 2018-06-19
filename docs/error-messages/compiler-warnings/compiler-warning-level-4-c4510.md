---
title: Kompilatora (poziom 4) ostrzeżenie C4510 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4510
dev_langs:
- C++
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b280a15381f53b6836b321e25717cbed19c7271
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297284"
---
# <a name="compiler-warning-level-4-c4510"></a>Kompilator C4510 ostrzegawcze (poziom 4)
"class": nie można wygenerować konstruktora domyślnego  
  
 Kompilator nie może wygenerować domyślnego konstruktora dla określonej klasy, a żaden konstruktor zdefiniowany przez użytkownika została utworzona. Nie można utworzyć obiektów tego typu.  
  
 Istnieje kilka sytuacji, w których uniemożliwić kompilatorowi wygenerowanie konstruktora domyślnego w tym:  
  
-   Stały element członkowski danych.  
  
-   Element członkowski danych, który jest odwołanie.  
  
 Należy utworzyć użytkownika domyślnego konstruktora dla klasy, która inicjuje tych elementów członkowskich.  
  
 Poniższy przykład generuje C4510:  
  
```  
// C4510.cpp  
// compile with: /W4  
struct A {  
   const int i;  
   int &j;  
   A& operator=( const A& ); // C4510 expected  
   // uncomment the following line to resolve this C4510  
   // A(int ii, int &jj) : i(ii), j(jj) {}  
};   // C4510  
  
int main() {  
}  
```