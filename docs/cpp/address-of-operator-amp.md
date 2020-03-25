---
title: 'Operator address-of: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
ms.openlocfilehash: 4c9ae9aedaec202c8798ab454ee5df1a68278a6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181606"
---
# <a name="address-of-operator-amp"></a>Operator address-of: &amp;

## <a name="syntax"></a>Składnia

```
& cast-expression
```

## <a name="remarks"></a>Uwagi

Jednoargumentowy operator address-of ( **&** ) Pobiera adres operandu. Argument operacji operatora address-of może być oznaczeniem funkcji lub l-wartością, która określa obiekt, który nie jest polem bitowym.

Operator address-of może być stosowany tylko do zmiennych z typami podstawowymi, strukturami, klasami lub Unii, które są zadeklarowane na poziomie pliku lub w odniesieniu do tablic indeksów. W tych wyrażeniach wyrażenie stałe, które nie zawiera operatora address-of, może być dodawane lub odejmowane od wyrażenia adresu.

W przypadku zastosowania do funkcji lub wartości l, wynik wyrażenia jest typem wskaźnika (r-Value) pochodnym typu operandu. Na przykład, jeśli operand jest typu **char**, wynik wyrażenia jest typu wskaźnika do **char**. Operator address-of, stosowany do obiektów **const** lub **volatile** , oblicza do `const type *` lub `volatile type *`, gdzie **Type** jest typem oryginalnego obiektu.

Gdy operator address-of jest stosowany do kwalifikowanej nazwy, wynik zależy od tego, czy *kwalifikowana nazwa* określa statyczną składową. Jeśli tak, wynik jest wskaźnikiem do typu określonego w deklaracji elementu członkowskiego. Jeśli składowa nie jest statyczna, wynik jest wskaźnikiem do *nazwy* elementu członkowskiego klasy wskazanej przez *kwalifikowana nazwa klasy*. (Zobacz [wyrażenia podstawowe](../cpp/primary-expressions.md) , aby uzyskać więcej informacji na temat *kwalifikowanej klasy-Name*). Poniższy fragment kodu pokazuje, jak wynik różni się w zależności od tego, czy element członkowski jest statyczny:

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

W tym przykładzie wyrażenie `&PTM::fValue` zwraca typ `float *` zamiast `float PTM::*`, ponieważ `fValue` jest statycznym elementem członkowskim.

Adres przeciążonej funkcji można wykonać tylko wtedy, gdy jest jasne, która wersja funkcji jest przywoływana. Zobacz [przeciążanie funkcji](function-overloading.md) , aby uzyskać informacje na temat sposobu uzyskiwania adresu określonej przeciążonej funkcji.

Zastosowanie operatora address-of do typu referencyjnego daje ten sam wynik, co zastosowanie operatora do obiektu, do którego jest powiązane odwołanie. Na przykład:

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

Poniższy przykład używa operatora address-of do przekazania argumentu wskaźnika do funkcji:

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

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Deklarator odwołania do wartości L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Operatory pośrednie i „Address-of”](../c-language/indirection-and-address-of-operators.md)
