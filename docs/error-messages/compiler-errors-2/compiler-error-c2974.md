---
title: "C2974 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2974
dev_langs: C++
helpviewer_keywords: C2974
ms.assetid: 1b444260-f2bf-48d7-ab1e-35573d8c4a0e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e24e25816ac646bcf26099abbfa8e681fdd72a6e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2974"></a>C2974 błąd kompilatora
Nieprawidłowy typ argumentu "number", oczekiwano typu  
  
 Argument rodzajowy lub szablonu nie jest zgodna deklaracja ogólne lub szablonu. Typ powinny być wyświetlane w nawiasach kwadratowych kąta. Sprawdź definicję ogólne lub szablonu, aby znaleźć poprawne typy.  
  
 Poniższy przykład generuje C2974:  
  
```  
// C2974.cpp  
// C2974 expected  
template <class T>  
struct TC {};  
  
template <typename T>  
void tf(T){}  
  
int main() {  
   // Delete the following 2 lines to resolve  
   TC<1>* tc;  
   tf<"abc">("abc");  
  
   TC<int>* tc;  
   tf<const char *>("abc");  
}  
```  
  
 C2974 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2974b.cpp  
// compile with: /clr  
// C2974 expected  
using namespace System;  
generic <class T>  
ref struct GCtype {};  
  
generic <typename T>  
void gf(T){}  
  
int main() {  
   // Delete the following 2 lines to resolve  
   GCtype<"a">^ gc;  
   gf<"a">("abc");  
  
   // OK  
   GCtype<int>^ gc;  
   gf<String ^>("abc");  
}  
```