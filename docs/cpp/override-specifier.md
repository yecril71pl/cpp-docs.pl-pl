---
title: Specyfikator przesłonięcia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d43620ceeb0404c3ad8b10cee3d0a00e7b2f467
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="override-specifier"></a>override, specyfikator
Można użyć `override` — słowo kluczowe do wyznaczenia elementu członkowskiego, funkcji, które przesłonić funkcję wirtualną w klasie podstawowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
function-declaration override;  
```  
  
## <a name="remarks"></a>Uwagi  
 `override` kontekstowa i ma specjalne znaczenie tylko wtedy, gdy jest używany po deklaracji funkcji Członkowskich; w przeciwnym razie nie jest zarezerwowanym słowem kluczowym.  
  
## <a name="example"></a>Przykład  
 Użyj `override` pomagające zapobiec nieumyślnemu dziedziczenia w kodzie. W poniższym przykładzie przedstawiono where, bez użycia `override`, zachowanie funkcji elementu członkowskiego klasy pochodnej mogą nie mieć zostały przeznaczone. Kompilator nie Emituj błędów dla tego kodu.  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA(); // ok, works as intended  
  
    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not  
                          // override BaseClass::funcB() const and it is a new member function  
  
    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different  
                                      // parameter type than BaseClass::funcC(int), so  
                                      // DerivedClass::funcC(double) is a new member function  
  
};  
  
```  
  
 Jeśli używasz `override`, kompilator generuje błędy zamiast dyskretnie tworzenia nowego elementu członkowskiego funkcji.  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA() override; // ok  
  
    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not   
                                   // override BaseClass::funcB() const  
  
    virtual void funcC( double = 0.0 ) override; // compiler error:   
                                                 // DerivedClass::funcC(double) does not   
                                                 // override BaseClass::funcC(int)  
  
    void funcD() override; // compiler error: DerivedClass::funcD() does not   
                           // override the non-virtual BaseClass::funcD()  
};  
  
```  
  
 Aby określić funkcje nie może zostać zastąpione i nie może być dziedziczona klas, użyj [końcowego](../cpp/final-specifier.md) — słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz też  
 [final, Specyfikator](../cpp/final-specifier.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 