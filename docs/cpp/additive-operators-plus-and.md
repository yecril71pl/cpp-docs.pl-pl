---
title: 'Operatory dodawania: + i - | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs: C++
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 02909b9b42ca781f7a178aa4b9dc7440bd89f2a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="additive-operators--and--"></a>Operatory dodawania: + i -
## <a name="syntax"></a>Składnia  
  
```  
expression + expression   
expression - expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Operatory dodawania są:  
  
-   Dodawanie (**+**)  
  
-   Odejmowanie (**-**)  
  
 Te operatory dwuargumentowe mają łączność od lewej do prawej.  
  
 Operatory dodawania zająć argumentów operacji typu arytmetycznego lub wskaźnikowego. Wynik operacji dodawania (**+**) operator to suma argumentów operacji. Wynik odejmowania (**-**) — operator różni się od argumenty operacji. Jeśli co najmniej jeden z argumentów jest wskaźników, wskaźników do obiektów, a nie do funkcji muszą być. Jeśli oba argumenty są wskaźnikami, wyniki nie są łatwy do rozpoznania, chyba że obydwa są wskaźnikami do obiektów w tej samej tablicy.  
  
 Operatory dodawania zająć argumentów operacji *arytmetyczne*, *integralną*, i *skalarne* typów. Są one zdefiniowane w poniższej tabeli.  
  
### <a name="types-used-with-additive-operators"></a>Typy używane z operatory dodawania  
  
|Typ|Znaczenie|  
|----------|-------------|  
|*operacje arytmetyczne*|Typów całkowitych i zmiennoprzecinkowych są nazywane zbiorczo "arytmetycznego" typów.|  
|*wartości całkowitych*|Typy char i int (krótki czas,) i wyliczenia są typy "zintegrowane".|  
|*skalarne*|Argumenty skalarne są argumentów operacji typu arytmetycznego lub wskaźnikowego.|  
  
 Prawne kombinacje operatorów te są:  
  
 *arytmetyczny* + *arytmetyczne*  
  
 *skalarne* + *wartości całkowitych*  
  
 *całkowite* + *skalarne*  
  
 *arytmetyczny* - *arytmetyczne*  
  
 *skalarne* - *skalarne*  
  
 Należy pamiętać, że dodawanie i odejmowanie nie są równoważne operacji.  
  
 Jeśli oba argumenty typu arytmetycznego, konwersje objęte [konwersje standardowe](standard-conversions.md) są stosowane do argumentów operacji, a wynik jest typu przekonwertowany.  
  
## <a name="example"></a>Przykład  
  
```  
// expre_Additive_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
#define SIZE 5  
using namespace std;  
int main() {  
   int i = 5, j = 10;  
   int n[SIZE] = { 0, 1, 2, 3, 4 };  
   cout  << "5 + 10 = " << i + j << endl  
         << "5 - 10 = " << i - j << endl;  
  
   // use pointer arithmetic on array  
  
   cout << "n[3] = " << *( n + 3 ) << endl;  
}  
```  
  
## <a name="pointer-addition"></a>Dodawanie wskaźników  
 Jeśli jeden z argumentów operacji dodawania jest wskaźnik do tablicy obiektów, innych musi być typu całkowitego. Wynik ma postać wskaźnika jest taki sam typ jak oryginalny wskaźnik i wskazującego do innego elementu tablicy. Poniższy fragment kodu przedstawia tę koncepcję:  
  
```  
short IntArray[10]; // Objects of type short occupy 2 bytes  
short *pIntArray = IntArray;  
  
for( int i = 0; i < 10; ++i )  
{  
    *pIntArray = i;  
    cout << *pIntArray << "\n";  
    pIntArray = pIntArray + 1;  
}  
```  
  
 Mimo że całkowitą wartość 1 jest dodawana do `pIntArray`, nie oznacza to "Dodaj 1 na adres"; zamiast oznacza "dostosować kursor do następnego obiektu w tablicy" takiej sytuacji należy 2 bajty (lub `sizeof( int )`) optymalizacji.  
  
> [!NOTE]
>  Kod w postaci `pIntArray = pIntArray + 1` rzadko zostanie znaleziony w programach języka C++; przeprowadzić przyrostu te formularze są preferowane: `pIntArray++` lub `pIntArray += 1`.  
  
## <a name="pointer-subtraction"></a>Odejmowanie wskaźnika  
 Jeśli oba argumenty są wskaźnikami, wynik odejmowania różni się (w elementach tablicy) argumenty operacji. Wyrażenie odejmowania daje podpisem integralną wyniku ptrdiff_t — typ (zdefiniowany w pliku dołączanego standardowe STDDEF. H).  
  
 Jeden z argumentów może być typu całkowitego, tak długo, jak jest drugi argument operacji. Wynik odejmowania jest taki sam typ jak oryginalny wskaźnika. Wartość odejmowania jest wskaźnik do (*n* - *i*) th elementu tablicy, której  *n*  jest element wskazywana przez Oryginalny wskaźnik i *i* jest integralną wartość drugiego argumentu operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Dwuargumentowymi](../cpp/expressions-with-binary-operators.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory dodawania języka C](../c-language/c-additive-operators.md)
