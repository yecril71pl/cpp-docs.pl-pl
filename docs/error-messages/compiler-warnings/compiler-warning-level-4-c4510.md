---
title: "Kompilatora (poziom 4) ostrzeżenie C4510 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4510
dev_langs: C++
helpviewer_keywords: C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4bfef2780f338357b600f8fae28559d4c7c00e49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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