---
title: "C2761 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2761
dev_langs: C++
helpviewer_keywords: C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7670c3fa67579c218024dfd3f1f585ad57cf37e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2761"></a>C2761 błąd kompilatora
"Funkcja": niedozwolone funkcji członkowskiej  
  
 Nie można ponownie zadeklarować funkcji członkowskiej. Można zdefiniować ją, ale nie ponownie zadeklarować.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2761.  
  
```  
// C2761.cpp  
class a {  
   int t;  
   void test();  
};  
  
void a::a;     // C2761  
void a::test;  // C2761  
  
```  
  
## <a name="example"></a>Przykład  
 Nie można zdefiniować Niestatyczne elementy członkowskie klasy lub struktury.  Poniższy przykład generuje C2761.  
  
```  
// C2761_b.cpp  
// compile with: /c  
struct C {  
   int s;  
   static int t;  
};  
  
int C::s;   // C2761  
int C::t;   // OK  
```