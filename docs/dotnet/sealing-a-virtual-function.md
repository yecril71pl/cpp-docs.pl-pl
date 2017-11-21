---
title: "Pieczętowanie funkcji wirtualnej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sealed keyword [C++]
- derived classes, virtual functions
- virtual functions, sealing
- __sealed keyword
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 500e5b5e6014b7141c000a4e453341ceb5e822d0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="sealing-a-virtual-function"></a>Pieczętowanie funkcji wirtualnej
Składnia pieczętowanie funkcji wirtualnej został zmieniony z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 `__sealed` — Słowo kluczowe jest używane w zarządzanych rozszerzeń do modyfikowania albo typ referencyjny, brak zezwolenia kolejnych pochodnym od niego (zobacz [deklaracji typu klasy zarządzane](../dotnet/declaration-of-a-managed-class-type.md)), lub zmodyfikować funkcją wirtualną Brak zezwolenia kolejne Zastępowanie metody w klasie pochodnej. Na przykład:  
  
```  
__gc class base { public: virtual void f(); };  
__gc class derived : public base {  
public:  
   __sealed void f();  
};  
```  
  
 W tym przykładzie `derived::f()` zastępuje `base::f()` wystąpienia oparte na dokładnego dopasowania prototypu funkcji. `__sealed` — Słowo kluczowe wskazuje, że kolejne klasę dziedziczoną z klasy pochodnej nie może dostarczyć zastępująca `derived::f()`.  
  
 W nowej składni `sealed` jest umieszczany po podpis niż uzyskaniem dostępu do występować w dowolnym miejscu przed prototypu rzeczywista funkcja, ponieważ wcześniej było dozwolone. Ponadto użycie `sealed` wymaga jawnego użycia `virtual` również — słowo kluczowe. Oznacza to, że poprawne tłumaczenie `derived`powyżej, jest następujący:  
  
```  
ref class derived: public base {  
public:  
   virtual void f() override sealed;  
};  
```  
  
 Brak `virtual` — słowo kluczowe, w tym wystąpieniu powoduje wystąpienie błędu. W nowej składni kontekstowe słowo kluczowe `abstract` można użyć zamiast `=0` wskazująca czystej funkcji wirtualnej. To nie jest obsługiwana w ramach rozszerzeń zarządzanych. Na przykład:  
  
```  
__gc class base { public: virtual void f()=0; };  
```  
  
 należy ponownie zapisać jako  
  
```  
ref class base { public: virtual void f() abstract; };  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje członków w obrębie klasy lub interfejsu (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [zapieczętowane](../windows/sealed-cpp-component-extensions.md)