---
title: "złożone&lt;podwójne&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: complex/std::complex<double>
dev_langs: C++
helpviewer_keywords: complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b279b78c309dd9fff87954d9b50b255b7f0d9f25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="complexltdoublegt"></a>złożone&lt;podwójne&gt;
Opisuje obiekt, który przechowuje uporządkowanej parę obiektów zarówno typu **podwójne***,* najpierw reprezentujący część liczby złożonej, a drugi rzeczywista reprezentujący urojony części.  
  
## <a name="syntax"></a>Składnia  
  
```
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as template class complex
};
```  
  
#### <a name="parameters"></a>Parametry  
 `RealVal`  
 Wartość typu **podwójne** rzeczywistych część liczby złożonej tworzona.  
  
 `ImagVal`  
 Wartość typu **podwójne** urojony część liczby złożonej tworzona.  
  
 `complexNum`  
 Liczby złożonej typu **float** lub typu `long double` których części rzeczywistą i urojony są używane do zainicjowania liczbą typu **podwójne** tworzona.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba złożonych typu **podwójne**.  
  
## <a name="remarks"></a>Uwagi  
 Jawna specjalizacja szablonu klasy złożone, aby złożonych klasy typu **podwójne** różni się od klasy szablonu tylko w przypadku konstruktorów definiuje. Konwersja z **float** do **podwójne** może być pośrednie, ale konwersja z `long double` do **podwójne** musi być **jawne** . Korzystanie z **jawne** wyklucza rozpoczęciu konwersji typu przy użyciu składni przypisania.  
  
 Aby uzyskać więcej informacji na klasy szablonu `complex`, zobacz [klasy złożone](../standard-library/complex-class.md). Aby uzyskać listę elementów członkowskich klasy szablonu `complex`, zobacz.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// complex_comp_dbl.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <double> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type double gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type float  
   complex <float> c2float ( 4.0 , 5.0 );  
   complex <double> c2double ( c2float );  
   cout << "Implicit conversion from type float to type double,"  
        << "\n gives c2double = " << c2double << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type long double  
   complex <long double> c3longdouble ( 4.0 , 5.0 );  
   complex <double> c3double ( c3longdouble );  
   cout << "Explicit conversion from type float to type double,"  
        << "\n gives c3longdouble = " << c3longdouble << endl;  
  
   // The modulus and argument of a complex number can be recovered  
   double absc3 = abs ( c3longdouble );  
   double argc3 = arg ( c3longdouble );  
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "  
        << absc3 << endl;  
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "  
        << argc3 << " radians, which is " << argc3 * 180 / pi  
        << " degrees." << endl;  
}  
\* Output:   
Specifying initial real & imaginary parts,  
 as type double gives c1 = (4,5)  
Implicit conversion from type float to type double,  
 gives c2double = (4,5)  
Explicit conversion from type float to type double,  
 gives c3longdouble = (4,5)  
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312  
Argument of c3 is recovered from c3 using:  
 arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.  
*\  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: \<złożonych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [COMPLEX — klasa](../standard-library/complex-class.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



