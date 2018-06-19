---
title: Kompilatora (poziom 4) ostrzeżenie C4706 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4706
dev_langs:
- C++
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1131147a9600525746cb3e89119189ed9e5026a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296972"
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