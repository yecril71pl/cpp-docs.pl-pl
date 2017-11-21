---
title: "C2871 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2871
dev_langs: C++
helpviewer_keywords: C2871
ms.assetid: 44aeb84d-61f0-45e0-8dad-22a3cd46b7f8
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0003f04a32ff017234607a90162465549092a013
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2871"></a>C2871 błąd kompilatora
"Nazwa": przestrzeń nazw o tej nazwie nie istnieje.  
  
Ten błąd wystąpi podczas przekazywania identyfikator, który nie jest przestrzenią nazw do [przy użyciu](../../cpp/namespaces-cpp.md#using_directives) dyrektywy.  
  
## <a name="example"></a>Przykład  
Poniższy przykład generuje C2871:  
  
```cpp  
// C2871.cpp  
// compile with: /c
namespace a {
   int fn(int i) { return i; }
} 
namespace b { 
   using namespace d;   // C2871 because d is not a namespace  
   using namespace a;   // OK
}  
```