---
title: 'Operatory wskaźnika do elementu członkowskiego: .* i -&gt;*'
ms.date: 11/04/2016
f1_keywords:
- .*
- ->*
helpviewer_keywords:
- expressions [C++], pointer
- pointer-to-member operators [C++]
- .* operator
- expressions [C++], operators
- ->* operator
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
ms.openlocfilehash: 2100933bf525f0717978528301049085eaecd4f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320341"
---
# <a name="pointer-to-member-operators--and--gt"></a>Operatory wskaźnika do elementu członkowskiego: .* i -&gt;*

## <a name="syntax"></a>Składnia

```
expression .* expression
expression ->* expression
```

## <a name="remarks"></a>Uwagi

Operatory typu wskaźnik-element, .* i ->\*, zwracają wartość określonego elementu członkowskiego klasy dla obiektu określonego po lewej stronie wyrażenia.  Po prawej stronie należy określić składową klasy.  Poniższy przykład ilustruje sposób używania operatorów:

```cpp
// expre_Expressions_with_Pointer_Member_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

class Testpm {
public:
   void m_func1() { cout << "m_func1\n"; }
   int m_num;
};

// Define derived types pmfn and pmd.
// These types are pointers to members m_func1() and
// m_num, respectively.
void (Testpm::*pmfn)() = &Testpm::m_func1;
int Testpm::*pmd = &Testpm::m_num;

int main() {
   Testpm ATestpm;
   Testpm *pTestpm = new Testpm;

// Access the member function
   (ATestpm.*pmfn)();
   (pTestpm->*pmfn)();   // Parentheses required since * binds
                        // less tightly than the function call.

// Access the member data
   ATestpm.*pmd = 1;
   pTestpm->*pmd = 2;

   cout  << ATestpm.*pmd << endl
         << pTestpm->*pmd << endl;
   delete pTestpm;
}
```

## <a name="output"></a>Dane wyjściowe

```Output
m_func1
m_func1
1
2
```

W poprzednim przykładzie, wskaźnik do elementu członkowskiego, `pmfn`, jest używany do wywoływania funkcji członkowskiej `m_func1`. Inny wskaźnik do elementu członkowskiego, `pmd`, jest używany w celu uzyskania dostępu do członka `m_num`.

Operator binarny .* łączy pierwszy argument operacji, który musi być obiektem typu klasy, z drugim argumentem operacji, który musi być typem wskaźnika do składowej.

Operator binarny ->* łączy swój pierwszy operand, który musi być wskaźnikiem do obiektu typu klasy, z jego drugim operandem, który musi być typem wskaźnika do elementu członkowskiego.

W wyrażeniu zawierającym operator .* pierwszy argument operacji musi być typem klasy oraz zapewniać dostęp dla wskaźnika do składowej określonej w drugim argumencie operacji lub być typem jednoznacznie pochodnym i dostępnym dla tej klasy.

W wyrażeniu zawierającym operator ->* pierwszy operand musi być typu "wskaźnik do typu klasy" typu określonego w drugim operandie lub musi być typu jednoznacznie wywodzącego się z tej klasy.

## <a name="example"></a>Przykład

Rozważmy następujące klasy i fragment programu:

```cpp
// expre_Expressions_with_Pointer_Member_Operators2.cpp
// C2440 expected
class BaseClass {
public:
   BaseClass(); // Base class constructor.
   void Func1();
};

// Declare a pointer to member function Func1.
void (BaseClass::*pmfnFunc1)() = &BaseClass::Func1;

class Derived : public BaseClass {
public:
   Derived();  // Derived class constructor.
   void Func2();
};

// Declare a pointer to member function Func2.
void (Derived::*pmfnFunc2)() = &Derived::Func2;

int main() {
   BaseClass ABase;
   Derived ADerived;

   (ABase.*pmfnFunc1)();   // OK: defined for BaseClass.
   (ABase.*pmfnFunc2)();   // Error: cannot use base class to
                           // access pointers to members of
                           // derived classes.

   (ADerived.*pmfnFunc1)();   // OK: Derived is unambiguously
                              // derived from BaseClass.
   (ADerived.*pmfnFunc2)();   // OK: defined for Derived.
}
```

Wynik .* lub ->\* operatorów wskaźnika do elementu członkowskiego jest obiektem lub funkcją typu określonego w deklaracji wskaźnika do elementu członkowskiego. Zatem w powyższym przykładzie, wynik wyrażenia `ADerived.*pmfnFunc1()` jest wskaźnikiem do funkcji, która zwraca wartość void. Ten wynik jest wartością l, jeśli drugi argument operacji jest wartością l.

> [!NOTE]
> Jeżeli wynik jednego z operatorów wskaźnika do elementu członkowskiego jest funkcją, wynik może używany tylko jako argument operatora wywołania funkcji.

## <a name="see-also"></a>Zobacz też

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
