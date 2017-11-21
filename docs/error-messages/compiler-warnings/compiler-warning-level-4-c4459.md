---
title: "Kompilatora (poziom 4) ostrzeżenie C4459 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4459
dev_langs: C++
helpviewer_keywords: C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 11a4122bf58ac5645c4430f8c6a41de7ed19f430
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4459"></a>Kompilator C4459 ostrzegawcze (poziom 4)
  
> Deklaracja "*identyfikator*" powoduje ukrycie deklaracji globalnej
  
Deklaracja *identyfikator* w zakresie lokalnej powoduje ukrycie deklaracji o takiej samej nazwie *identyfikator* w zakresie globalnym. To ostrzeżenie informuje o tym, który odwołuje się do *identyfikator* w tym zakresie rozpoznać lokalnie zadeklarowanych wersji, a nie wersji globalnej, który może lub nie jest celem użytkownika. Ogólnie rzecz biorąc zaleca się zminimalizować użycie zmiennych globalnych dobrym rozwiązaniem engineering. Aby zminimalizować zanieczyszczenie globalnej przestrzeni nazw, zaleca się użycie nazwanych przestrzeni nazw dla zmiennych globalnych.  
  
To ostrzeżenie jest nowe w programie Visual Studio 2015, w programie Visual C++ wersja kompilatora godziny 18.00. Aby tłumienie ostrzeżeń z danej wersji kompilatora lub później, podczas migracji z kodu, należy użyć [/WV: 18](../../build/reference/compiler-option-warning-level.md) — opcja kompilatora. 

## <a name="example"></a>Przykład
  
 Poniższy przykład generuje C4459:  
  
```cpp  
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() { 
    int global_or_local; // warning C4459 
    global_or_local = 2;
} 
```  
  
Jednym ze sposobów rozwiązania tego problemu jest utworzenie przestrzeni nazw dla Twojego zmienne globalne, ale nie `using` dyrektywy do zapewnienia tego obszaru nazw zakresu, tak aby wszystkie odwołania musi używać jednoznaczne kwalifikowanej nazwy:  
  
```cpp  
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() { 
    int global_or_local; // OK 
    global_or_local = 2;
    globals::global_or_local = 3;
} 
```  
