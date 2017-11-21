---
title: "C3063 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3063
dev_langs: C++
helpviewer_keywords: C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 26d30e56c3e694b39f583b29d8bd378b6dcaee0f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3063"></a>C3063 błąd kompilatora
operator "operator": wszystkie operandy muszą posiadać ten sam typ wyliczeniowy  
  
Używając operatory na moduły wyliczające, obydwa argumenty operacji musi być typem wyliczenia. Aby uzyskać więcej informacji, zobacz [porady: Definiowanie wyliczeń i korzystanie w języku C + +/ CLI](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
Poniższy przykład generuje C3063 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3063.cpp  
// compile with: /clr  
enum class E { a, b } e, mask;  
int main() {  
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```