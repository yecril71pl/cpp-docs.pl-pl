---
title: "C3492 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3492
dev_langs:
- C++
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd8b70a22f24e41889c2c6d13cbb5fc2ff3e85e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3492"></a>C3492 błąd kompilatora
"var": nie można dokonać przechwytu elementu członkowskiego z anonimowego związku  
  
 Nie można dokonać przechwytu elementu Członkowskiego Unii bez nazwy.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Nadaj nazwę Unii i podaj pełną strukturę Unii do listy przechwytywania lambda wyrażenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3492, ponieważ znajdują się członkiem związek anonimowy:  
  
```  
// C3492a.cpp  
  
int main()  
{  
   union  
   {  
      char ch;  
      int x;  
   };  
  
   ch = 'y';  
   [&x](char ch) { x = ch; }(ch); // C3492  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia rozwiązanie C3492 przez nadanie Unii nazwy i przekazując pełną strukturę Unii do listy przechwytywania lambda wyrażenia:  
  
```  
// C3492b.cpp  
  
int main()  
{  
   union  
   {  
      char ch;  
      int x;  
   } u;  
  
   u.ch = 'y';  
   [&u](char ch) { u.x = ch; }(u.ch);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)