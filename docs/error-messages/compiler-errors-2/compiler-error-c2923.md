---
title: "C2923 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2923
dev_langs: C++
helpviewer_keywords: C2923
ms.assetid: 6b92933b-13ef-4124-99d9-b89f9fdae030
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 84a0e844161ea13fdc2515fa6ea403adf2e5caa1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2923"></a>C2923 błąd kompilatora
'type': 'Identyfikator' nie jest prawidłowy szablon typem argumentu dla parametru "param"  
  
 Lista argumentów brakuje typu potrzebne do utworzenia wystąpienia szablonu lub rodzajowa. Sprawdź szablon lub deklaracja ogólna.  
  
 Poniższy przykład generuje C2923:  
  
```  
// C2923.cpp  
template <class T> struct TC {};  
int x;  
int main() {  
   TC<x>* tc2;   // C2923  
   TC<int>* tc2;   // OK  
}  
```  
  
 C2923 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2923b.cpp  
// compile with: /clr /c  
generic <class T> ref struct GC {};  
  
int x;  
  
int main() {  
   GC<x>^ gc2;   // C2923  
   GC<int>^ gc2;   // OK  
}  
```