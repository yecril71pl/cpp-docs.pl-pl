---
title: "C2396 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2396
dev_langs: C++
helpviewer_keywords: C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20eca11d402265bbc81d61a8079ae9975cceef67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2396"></a>C2396 błąd kompilatora
"your_type::operator'type": CLR lub WinRT functionnot zdefiniowane przez użytkownika konwersja prawidłowe. Należy konwertować z albo konwertować na: t ^ ", t ^ %", t ^ & ", gdzie T ="your_type"  
  
 Funkcji konwersji w środowiska wykonawczego systemu Windows lub typ zarządzany nie ma co najmniej jeden parametr, którego typ jest taki sam jak typ zawierający funkcję konwersji.  
  
 Poniższy przykład generuje C2396 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2396.cpp  
// compile with: /clr /c  
  
ref struct Y {  
   static operator int(char c);   // C2396  
  
   // OK  
   static operator int(Y^ hY);  
   // or  
   static operator Y^(char c);  
};  
```