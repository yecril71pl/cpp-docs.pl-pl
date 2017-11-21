---
title: "Kompilatora (poziom 1) ostrzeżenie C4661 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4661
dev_langs: C++
helpviewer_keywords: C4661
ms.assetid: 603bb8b7-356d-4eef-924b-64d769bac5bd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f3cbb43bc99e1b345614a99dd7ae9405bfaf61cb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4661"></a>Kompilator C4661 ostrzegawcze (poziom 1)
'Identyfikator': Brak odpowiedniej definicji dostarczonej dla jawnego żądania wystąpienia szablonu  
  
 Element członkowski szablonu klasy nie jest zdefiniowany.  
  
## <a name="example"></a>Przykład  
  
```  
// C4661.cpp  
// compile with: /W1 /LD  
template<class T> class MyClass {  
public:  
   void i();   // declaration but not definition  
};  
template MyClass< int >;  // C4661  
```