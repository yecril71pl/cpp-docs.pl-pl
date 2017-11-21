---
title: "C3539 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3539
dev_langs: C++
helpviewer_keywords: C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 03283217be6aabbf216e2e60ad47abfc01a961d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3539"></a>C3539 błąd kompilatora
'type': argument szablonu nie może być typu, który zawiera "auto"  
  
 Typ argumentu wskazany szablon nie może zawierać użycie `auto` — słowo kluczowe.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Nie określaj argument szablonu z `auto` — słowo kluczowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca C3539.  
  
```  
// C3539.cpp  
// Compile with /Zc:auto  
template<class T> class C{};  
int main()  
{  
   C<auto> c;   // C3539  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Auto — słowo kluczowe](../../cpp/auto-keyword.md)