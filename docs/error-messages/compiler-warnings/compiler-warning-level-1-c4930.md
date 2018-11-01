---
title: Kompilator ostrzeżenie (poziom 1) C4930
ms.date: 11/04/2016
f1_keywords:
- C4930
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
ms.openlocfilehash: 15cd1ed61c747e2c9168b9fc0fee03dca8403a24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560176"
---
# <a name="compiler-warning-level-1-c4930"></a>Kompilator ostrzeżenie (poziom 1) C4930

"prototyp": prototypowana funkcja nie wywołana (czy definicja zmiennej była przeznaczona?)

Kompilator wykrył prototypu funkcji nieużywane. Jeśli prototyp była zamierzona jako deklaracja zmiennej, Usuń nawiasy otwarte i zamknięte.

Poniższy przykład spowoduje wygenerowanie C4930:

```
// C4930.cpp
// compile with: /W1
class Lock {
public:
   int i;
};

void f() {
   Lock theLock();   // C4930
   // try the following line instead
   // Lock theLock;
}

int main() {
}
```

C4930 może również wystąpić, gdy kompilator nie rozróżnia deklarację prototyp funkcji i wywołanie funkcji.

Poniższy przykład spowoduje wygenerowanie C4930:

```
// C4930b.cpp
// compile with: /EHsc /W1

class BooleanException
{
   bool _result;

public:
   BooleanException(bool result)
      : _result(result)
   {
   }

   bool GetResult() const
   {
      return _result;
   }
};

template<class T = BooleanException>
class IfFailedThrow
{
public:
   IfFailedThrow(bool result)
   {
      if (!result)
      {
         throw T(result);
      }
   }
};

class MyClass
{
public:
   bool MyFunc()
   {
      try
      {
         IfFailedThrow<>(MyMethod()); // C4930

         // try one of the following lines instead
         // IfFailedThrow<> ift(MyMethod());
         // IfFailedThrow<>(this->MyMethod());
         // IfFailedThrow<>((*this).MyMethod());

         return true;
      }
      catch (BooleanException e)
      {
         return e.GetResult();
      }
   }

private:
   bool MyMethod()
   {
      return true;
   }
};

int main()
{
   MyClass myClass;
   myClass.MyFunc();
}
```

W powyższym przykładzie wynik metody, która nie przyjmuje argumentów, zerowego jest przekazywany jako argument do konstruktora obiektu w zmiennej bez nazwy klasy lokalnej. Wywołanie może być rozróżniane przy nazwy zmiennej lokalnej lub poprzedzania ich wywołania metody, za pomocą wystąpienia obiektu wraz z odpowiednich operatorów wskaźnika do elementu członkowskiego.