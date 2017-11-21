---
title: "Ostrzeżenie (poziom 2 i 4) kompilatora — od C4200 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4200
dev_langs: C++
helpviewer_keywords: C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dfeb1c5b11c357d9b8321da8f0ff94fd44df9db9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Ostrzeżenie (poziom 2 i 4) kompilatora — od C4200
użyto niestandardowego rozszerzenia: tablica o rozmiarze zero w struktury/Unii  
  
 Wskazuje, że struktura lub związek zawiera tablicę, która ma rozmiar zerowy.  
  
 Deklaracja tablicy o rozmiarze zerowym to rozszerzenie firmy Microsoft. Powoduje to ostrzeżenie poziomu 2 podczas kompilowania pliku C++ i poziom 4 ostrzeżenie podczas kompilowania pliku C. To ostrzeżenie daje również kompilacji C++: "Nie można wygenerować elementu ctor kopiowania operatora przypisania kopii gdy UDT zawiera zerowy rozmiar tablicy." W tym przykładzie generuje ostrzeżenie — od C4200:  
  
```cpp  
// C4200.cpp  
// compile by using: cl /W4 c4200.cpp  
struct A {  
    int a[0];  // C4200  
};  
int main() {  
}  
```  
  
 To rozszerzenie niestandardowe jest często używane do kodu interfejsu za pomocą struktury danych zewnętrznych, które mają o zmiennej długości. Ten scenariusz dotyczy kodu, można wyłączyć ostrzeżenia:  
  
## <a name="example"></a>Przykład  
  
```cpp  
// C4200b.cpp  
// compile by using: cl /W4 c4200a.cpp  
#pragma warning(disable : 4200)  
struct A {  
    int a[0];  
};  
int main() {  
}  
```