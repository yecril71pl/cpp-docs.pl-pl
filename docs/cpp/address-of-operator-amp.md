---
title: 'Operator Address-of: &amp; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '&'
dev_langs:
- C++
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f194041633b251320ae5fb7889e569a105230373
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019825"
---
# <a name="address-of-operator-amp"></a>Operator Address-of: &amp;

## <a name="syntax"></a>Składnia

```
& cast-expression
```

## <a name="remarks"></a>Uwagi

Jednoargumentowy operator address-of (**&**) przyjmuje adres jego operandu. Operand operatora address-of może być określeniem funkcji lub l wartość opisująca obiekt, który nie jest polem bitowym.

Operator address-of można stosować tylko do zmiennych o strukturze podstawowych, klasy lub typy Unii, które są zadeklarowane na poziomie zakresu pliku lub do indeksowanych odwołań do tablic. W tych wyrażeniach wyrażenie stałe, które nie zawiera operatora address-of można dodać do lub odjęte od wyrażenia adresu.

Po zastosowaniu do funkcji lub l wartości, wynikiem wyrażenia typu wskaźnika (r) pochodzi od typu operand. Na przykład, jeśli argument jest typu **char**, wynikiem wyrażenia jest typ wskaźnika do **char**. Operator address-of, dotyczą **const** lub **volatile** obiektów, daje w wyniku `const type *` lub `volatile type *`, gdzie **typu** jest typ pierwotny obiekt.

Po zastosowaniu operatora address-of kwalifikowaną nazwę, wynik zależy od tego, czy *kwalifikowana nazwa* określa statyczny element członkowski. Jeśli tak, wynik jest wskaźnikiem do typu określonego w deklaracji elementu członkowskiego. Jeśli element członkowski nie jest statyczna, wynik jest wskaźnikiem do elementu członkowskiego *nazwa* klasy wskazanego przez *kwalifikowana class-name*. (Zobacz [wyrażenia podstawowe](../cpp/primary-expressions.md) więcej informacji na temat *kwalifikowana class-name*.) Poniższy fragment kodu przedstawia, jak wynik różnią się zależnie od tego, czy jest statyczny element członkowski:

```cpp
// expre_Address_Of_Operator.cpp
// C2440 expected
class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}
```

W tym przykładzie wyrażenie `&PTM::fValue` daje typu `float *` zamiast typu `float PTM::*` ponieważ `fValue` jest składową statyczną.

Adres przeciążonej funkcji mogą być wykonywane tylko wtedy, gdy jest to oczywiste, jest ono przywoływane wersji funkcji. Zobacz [przeciążanie funkcji](function-overloading.md) informacji o tym, jak w celu uzyskania adresu określonego przeciążonej funkcji.

Zastosowanie operatora address-of do typu odwołania daje ten sam wynik w postaci zastosowania operatora do obiektu, z którym związane są odwołania. Na przykład:

## <a name="example"></a>Przykład

```cpp
// expre_Address_Of_Operator2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
```

## <a name="output"></a>Dane wyjściowe

```Output
&d equals &rd
```

W poniższym przykładzie użyto operatora address-of, aby przekazać argumentu będącego wskaźnikiem do funkcji:

```cpp
// expre_Address_Of_Operator3.cpp
// compile with: /EHsc
// Demonstrate address-of operator &

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
```

## <a name="output"></a>Dane wyjściowe

```Output
25
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Deklarator odwołania do wartości L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Operatory pośrednie i „Address-of”](../c-language/indirection-and-address-of-operators.md)