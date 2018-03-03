---
title: "Kompilatora (poziom 4) ostrzeżenie C4706 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4706
dev_langs:
- C++
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 824028fb7fd6d563a7f49017eb6b35d1443490bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4706"></a>Kompilator C4706 ostrzegawcze (poziom 4)
Przypisanie wewnątrz wyrażenia warunkowego  
  
 Wartość testu w wyrażeniu warunkowym jest wynik przypisania.  
  
 Przydział ma wartość (wartość po lewej stronie przypisania), który może służyć legalnie w innym wyrażeniu, w tym wyrażeniu testu.  
  
 Poniższy przykład generuje C4706:  
  
```  
// C4706a.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a  = b ) // C4706  
   {  
   }  
}  
```  
  
 Ostrzeżenie nastąpi, nawet jeśli dwukrotnie nawiasy warunku:  
  
```  
// C4706b.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a  =  b ) ) // C4706  
   {  
   }  
}  
```  
  
 Jeśli masz zamiar do testowania relacji i przypisywanie, aby nie używać `==` operatora. Na przykład następująca linia testy czy i b są równe:  
  
```  
// C4706c.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a == b )  
   {  
   }  
}  
```  
  
 Jeśli zamierzasz wprowadzić wartość wynik przypisania test testy w celu zapewnienia, że przydział jest różna od zera lub not null. Na przykład poniższy kod nie spowoduje to ostrzeżenie:  
  
```  
// C4706d.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a = b ) != 0 )  
   {  
   }  
}  
```