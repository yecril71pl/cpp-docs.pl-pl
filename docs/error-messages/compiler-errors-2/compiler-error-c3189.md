---
title: "C3189 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3189
dev_langs: C++
helpviewer_keywords: C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ad89c163dfaaa4eaa3a0304160c403977700fe95
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3189"></a>C3189 błąd kompilatora
"typeid\<typ abstrakcyjny deklarator >": Ta składnia nie jest już obsługiwana, należy użyć:: typeid zamiast niego  
  
 Przestarzałe formę [typeid](../../windows/typeid-cpp-component-extensions.md) był używany, za pomocą nowego formularza.  
  
 Poniższy przykład generuje C3189:  
  
```  
// C3189.cpp  
// compile with: /clr  
int main() {  
   System::Type^ t  = typeid<System::Object>;   // C3189  
   System::Type^ t2  = System::Object::typeid;   // OK  
}  
```