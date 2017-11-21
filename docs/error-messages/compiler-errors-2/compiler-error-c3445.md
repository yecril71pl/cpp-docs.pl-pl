---
title: "C3445 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3445
dev_langs: C++
helpviewer_keywords: C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e880eca87816973d531a2662486dde0ae7c77987
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3445"></a>C3445 błąd kompilatora
kopiowania listy Inicjalizacja "*typu*" nie można użyć jawny Konstruktor  
  
ISO standardzie C ++ 17 kompilator jest wymagane uwzględnienie jawny Konstruktor Rozpoznanie przeciążenia w Inicjalizacja listy kopii, ale musi Zgłoś błąd, jeśli faktycznie jest wybierany tego przeciążenia.  
  
Począwszy od programu Visual Studio 2017 kompilator znajduje błędy dotyczące tworzenia obiektów za pomocą listy inicjalizatora, które nie zostały odnalezione w programie Visual Studio 2015. Te błędy może prowadzić do awarii lub niezdefiniowane zachowanie w czasie wykonywania.

## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3445.  
  
```cpp  
// C3445.cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of 
                      //     'A' cannot use an explicit constructor
}
```  
  
Aby rozwiązać problem, należy użyć bezpośredniego inicjowania:  
  
```cpp  
// C3445b.cpp  
struct A
{
    explicit A(int) {} 
    A(double) {}
};

int main()
{
    A a1{ 1 };
}  
```  
  