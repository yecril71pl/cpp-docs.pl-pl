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
ms.openlocfilehash: 372dd9c789c54a38a5eed2c5f457c518989ede17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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