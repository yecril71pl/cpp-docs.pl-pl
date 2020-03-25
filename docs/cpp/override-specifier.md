---
title: override, specyfikator
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 82837ae34ab786e607df54038493b14350574a15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188483"
---
# <a name="override-specifier"></a>override, specyfikator

Możesz użyć słowa kluczowego **override** , aby wyznaczyć funkcje członkowskie, które zastępują funkcję wirtualną w klasie bazowej.

## <a name="syntax"></a>Składnia

```
function-declaration override;
```

## <a name="remarks"></a>Uwagi

**zastąpienie** jest zależne od kontekstu i ma specjalne znaczenie tylko wtedy, gdy jest używane po deklaracji funkcji składowej; w przeciwnym razie nie jest zarezerwowanym słowem kluczowym.

## <a name="example"></a>Przykład

Użyj funkcji **override** , aby zapobiec nieumyślnemu dziedziczeniu w kodzie. Poniższy przykład pokazuje, gdzie, bez użycia **przesłonięcia**, zachowanie funkcji składowej klasy pochodnej może nie być zamierzone. Kompilator nie emituje żadnych błędów dla tego kodu.

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

Gdy używasz **przesłonięcia**, kompilator generuje błędy zamiast dyskretnie tworzyć nowe funkcje członkowskie.

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

Aby określić, że funkcje nie mogą być zastępowane i że klasy nie mogą być dziedziczone, użyj słowa kluczowego [Final](../cpp/final-specifier.md) .

## <a name="see-also"></a>Zobacz też

[final, specyfikator](../cpp/final-specifier.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
