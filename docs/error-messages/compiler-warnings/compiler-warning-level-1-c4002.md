---
title: "Kompilatora (poziom 1) ostrzeżenie C4002 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4002
dev_langs: C++
helpviewer_keywords: C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bb1e3512074b2767977367b30ac5d01dc5758b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4002"></a>Kompilator C4002 ostrzegawcze (poziom 1)
zbyt wiele parametrów rzeczywistych dla makra "identyfikatora"  
  
 Liczba rzeczywistych parametrów w makrze przekracza liczbę parametrów formalnych w definicji makra. Zbiera preprocesora dodatkowe parametry ale ignoruje je w rozwinięciu makra.  
  
 C4002 mogą wystąpić podczas korzystania z niepoprawnie [makra Wariadyczne](../../preprocessor/variadic-macros.md).  
  
 Poniższy przykład generuje C4002:  
  
```  
// C4002.cpp  
// compile with: /W1  
#define test(a) (a)  
  
int main() {  
   int a = 1;  
   int b = 2;  
   a = test(a,b);   // C4002  
   // try..  
   a = test(a);  
}  
```  
  
 Ten błąd może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003: dodatkowe przecinkami w makrze już akceptowane.  
  
 Kompilator nie będzie akceptował dodatkowe przecinkami w makrze. Kod identyfikator był prawidłowy w Visual Studio .NET 2003 i wersji programu Visual Studio .NET programu Visual C++ Usuń dodatkowe przecinkami.  
  
```  
// C4002b.cpp  
// compile with: /W1  
#define F(x,y)  
int main()  
{  
   F(2,,,,,,3,,,,,,)   // C4002  
   // Try the following line instead:  
   // F(2,3)  
}  
```