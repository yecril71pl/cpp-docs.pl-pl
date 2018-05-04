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
ms.openlocfilehash: df243cac3b48a120345760f814a97b77667c770f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="address-of-operator-amp"></a>Operator Address-of: &amp;
## <a name="syntax"></a>Składnia  
  
```  
& cast-expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Jednoargumentowy operator address-of (**&**) ma adres jej argument. Argument operacji operatora adresu można oznaczeniem funkcji lub l wartość, która określa obiekt, który nie jest polem bitowym.  
  
 Operator address-of można stosować tylko do zmiennych z podstawowych, struktury, klasy, lub jako typami Unii, które są zadeklarowane na poziomie zakresu plików lub do odwołań do tablicy. W tych wyrażeń wyrażenie stałe, która nie zawiera operator address-of może być dodania lub odjęcia wyrażenia adresu.  
  
 Po zastosowaniu funkcji lub wartości l, wynikiem wyrażenia jest typem wskaźnika (r) pochodzi od typu argumentu. Na przykład, jeśli argument jest typu `char`, wynikiem wyrażenia jest typ wskaźnika do `char`. Operator address-of, dotyczą **const** lub `volatile` obiektów, daje w wyniku **const** `type` **\*** lub `volatile` `type` **\***, gdzie `type` jest typem obiektu oryginalnego.  
  
 Gdy operator address-of jest stosowany do [kwalifikowana nazwa](http://msdn.microsoft.com/en-us/3fefb16d-8120-4627-8b3f-3d90fbdcd1df), wynik jest zależny od tego, czy *nazwa kwalifikowana* określa statycznego elementu członkowskiego. Jeśli tak, wynik ma postać wskaźnika na typ określony w deklaracji elementu członkowskiego. Jeśli element członkowski nie jest statyczny, wynikiem jest wskaźnik do elementu członkowskiego *nazwa* klasy oznaczona *klasy nazwy kwalifikowanej*. (Zobacz [wyrażenia podstawowe](../cpp/primary-expressions.md) więcej informacji o *klasy nazwy kwalifikowanej*.) Poniższy fragment kodu przedstawia, jak wynik różni się w zależności od tego, czy element członkowski jest statyczny:  
  
```  
// expre_Address_Of_Operator.cpp  
// C2440 expected  
class PTM {  
public:  
           int   iValue;  
    static float fValue;  
};  
  
int main() {  
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static  
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static  
   float *spfValue     = &PTM::fValue;  // OK  
}  
```  
  
 W tym przykładzie wyrażenie `&PTM::fValue` daje typu `float *` zamiast typu `float PTM::*` ponieważ `fValue` jest statycznym elementem członkowskim.  
  
 Adres przeciążonej funkcji mogą być wykonywane tylko wtedy, gdy jest wyczyszczone, w którą wersję funkcji wystąpiło odwołanie do. Zobacz [przeciążanie funkcji](function-overloading.md) informacji o sposobie uzyskania adresu określonego przeciążonej funkcji.  
  
 Zastosowanie operator address-of na typ referencyjny daje takiego samego wyniku jako operator odnoszący się do obiektu, z którym związane są odwołania. Na przykład:  
  
## <a name="example"></a>Przykład  
  
```  
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
  
```  
&d equals &rd  
```  
  
 W poniższym przykładzie użyto operator address-of do przekazania argumentu będącego wskaźnikiem do funkcji:  
  
```  
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
  
```  
25  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Jednoargumentowymi](../cpp/expressions-with-unary-operators.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Deklarator odwołania do wartości: &](../cpp/lvalue-reference-declarator-amp.md)   
 [Operatory pośrednie i „Address-of”](../c-language/indirection-and-address-of-operators.md)
