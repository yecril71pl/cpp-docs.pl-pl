---
title: override, specyfikator
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 71505f8b9b4dc2800e80a78a64f0ca6984af1349
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345867"
---
# <a name="override-specifier"></a>override, specyfikator

Możesz użyć **zastąpienia** — słowo kluczowe, aby wyznaczyć element członkowski funkcji, które zastępują funkcję wirtualną w klasie bazowej.

## <a name="syntax"></a>Składnia

```
function-declaration override;
```

## <a name="remarks"></a>Uwagi

**Zastąp** jest zależny od kontekstu i ma specjalne znaczenie tylko wtedy, gdy jest używany po deklarację funkcji członkowskiej; w przeciwnym razie nie jest zarezerwowanym słowem kluczowym.

## <a name="example"></a>Przykład

Użyj **zastąpienia** pomagające zapobiec nieumyślnemu dziedziczeniu w kodzie. Poniższy przykład ukazuje gdzie, bez używania **zastąpienia**, zachowanie funkcji członkowskiej klasy pochodnej może nie być planowane. Kompilator nie emituje żadnych błędów dla tego kodu.

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

Kiedy używasz **zastąpienia**, kompilator generuje błędy zamiast dyskretnie tworzyć nowe funkcje Członkowskie.

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

Aby określić funkcje nie mogą być zastępowane i że klasy nie może być dziedziczona, użyj [końcowego](../cpp/final-specifier.md) — słowo kluczowe.

## <a name="see-also"></a>Zobacz także

[final, specyfikator](../cpp/final-specifier.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)