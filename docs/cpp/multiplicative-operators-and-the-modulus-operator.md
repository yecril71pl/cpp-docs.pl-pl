---
title: "Operatory mnożenia i Operator modulo | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '%'
- /
dev_langs: C++
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bb6ad2396b47932f05d9404485e4b32a7e92363b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>Operatory mnożenia i Operator modulo
## <a name="syntax"></a>Składnia  
  
```  
expression * expression   
expression / expression   
expression % expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Operatory multiplikatywne to:  
  
-   Mnożenia (**\***)  
  
-   Dzielenie (**/**)  
  
-   Modulo (resztę z dzielenia) (`%`)  
  
 Te operatory dwuargumentowe mają łączność od lewej do prawej.  
  
 Operatory multiplikatywne przyjmują operandy typów arytmetycznych. Operator modulo (`%`) ma bardziej rygorystycznych wymagań argumentów musi być typu całkowitego. (Aby uzyskać resztę z dzielenia liczb zmiennoprzecinkowych, użyj funkcji środowiska wykonawczego [fmod —](../c-runtime-library/reference/fmod-fmodf.md).) Konwersje objęte [konwersje standardowe](standard-conversions.md) są stosowane do argumentów operacji, a wynik jest typu przekonwertowany.  
  
 Operator mnożenia daje wynik mnożenia pierwszego operandu przez drugi.  
  
 Operator dzielenia daje wynik dzielenia pierwszego operandu przez drugi.  
  
 Operator modulo daje pozostałej przez następujące wyrażenie, gdzie *e1* jest pierwszy argument operacji i *e2* jest drugi: *e1* -(*e1*  /  *e2*) \* *e2*, gdzie są obydwa argumenty operacji typów całkowitych.  
  
 Dzielenie przez 0 w wyrażeniu dzielenia lub modulo jest nieokreślone i powoduje błąd w czasie wykonywania. Dlatego następujące wyrażenia generują nieokreślone, błędne wyniki:  
  
```  
i % 0  
f / 0.0  
```  
  
 Jeśli oba operandy wyrażenia mnożenia, dzielenia lub modulo mają taki sam znak, wynik jest dodatni. W przeciwnym razie wynik jest ujemny. Znak wyniku operacji modulo zależy od implementacji.  
  
> [!NOTE]
>  Ponieważ konwersje wykonywane przez operatory multiplikatywne nie przewidują warunków przepełnienia lub niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji multiplikatywnej nie może być przedstawiony w typie operandów po konwersji.  
  
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 W Microsoft C++, wynik wyrażenia modulo jest zawsze taki sam, jak znak pierwszego operandu.  
  
**KOŃCOWY określonych firmy Microsoft**  
 Jeśli obliczone dzielenie dwóch liczb całkowitych jest niedokładne i tylko jeden argument jest liczbą ujemną, wynik jest największą liczbą całkowitą (w wielkości, pomijając znak), mniejszą niż dokładna wartość, którą dałaby operacja dzielenia. Na przykład, obliczoną wartością -11 /-3.666666666 to 3. Wynik tego podziału integralną jest -3.  
  
 Relacja między operatory mnożenia jest określany przez tożsamość (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*.  
  
## <a name="example"></a>Przykład  
 Następujący program pokazuje operatory multiplikatywne. Należy pamiętać, że albo operandu `10 / 3` musi być jawnie rzutowany na typ `float` w celu uniknięcia obcięcie, tak aby oba argumenty typu `float` przed dzielenia.  
  
```  
// expre_Multiplicative_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main() {  
   int x = 3, y = 6, z = 10;  
   cout  << "3 * 6 is " << x * y << endl  
         << "6 / 3 is " << y / x << endl  
         << "10 % 3 is " << z % x << endl  
         << "10 / 3 is " << (float) z / x << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Dwuargumentowymi](../cpp/expressions-with-binary-operators.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory mnożenia języka C](../c-language/c-multiplicative-operators.md)