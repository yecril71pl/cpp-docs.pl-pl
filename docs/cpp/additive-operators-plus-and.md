---
title: 'Operatory dodawania: + i - | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89fc0f122f0859e6fc891ddfccd4bc99e7034bfe
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37948240"
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
  
 Operatory dodawania przyjmują operandy typu arytmetycznego lub wskaźnikowego. Wynik dodawania (**+**) operator jest sumę argumentów. Wynik odejmowania (**-**) — operator różni się od argumentów. Jeśli co najmniej jeden z argumentów są wskaźnikami, muszą być wskaźników do obiektów, a nie do funkcji. Jeśli oba operandy są wskaźnikami, wyniki nie są istotne, chyba że oba są wskaźnikami do obiektów w tej samej tablicy.  
  
 Operatory dodawania przyjmują operandy z *arytmetyczne*, *całkowitego*, i *skalarne* typów. Są one zdefiniowane w poniższej tabeli.  
  
### <a name="types-used-with-additive-operators"></a>Typy używane z operatorów dodawania  
  
|Typ|Znaczenie|  
|----------|-------------|  
|*Operacje arytmetyczne*|Typów całkowitych i zmiennoprzecinkowych są nazywane zbiorczo "arytmetyczne" typów.|  
|*integral*|Typy char i int (długi, krótki) i wyliczenia są typy "zintegrowane".|  
|*scalar*|Argumenty skalarne są argumentów operacji typu arytmetycznego lub wskaźnikowego.|  
  
 Prawne kombinacje tych operatorów są:  
  
 *arytmetyczny* + *arytmetyczne*  
  
 *scalar* + *integral*  
  
 *integral* + *scalar*  
  
 *arytmetyczny* - *arytmetyczne*  
  
 *scalar* - *scalar*  
  
 Należy pamiętać, że dodawanie i odejmowanie nie są równoważne operacji.  
  
 Jeśli oba operandy są typu arytmetycznego, konwersje omówione w [konwersje standardowe](standard-conversions.md) są stosowane do operandów, a wynik jest typu konwertowanego.  
  
## <a name="example"></a>Przykład  
  
```cpp 
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
 Jeśli jeden z argumentów operacji dodawania jest wskaźnik do tablicy obiektów, druga musi być typu całkowitego. Wynik jest wskaźnik jest taki sam typ co oryginalny wskaźnik i który wskazuje na inny element tablicy. Poniższy fragment kodu ilustruje tę koncepcję:  
  
```cpp 
short IntArray[10]; // Objects of type short occupy 2 bytes  
short *pIntArray = IntArray;  
  
for( int i = 0; i < 10; ++i )  
{  
    *pIntArray = i;  
    cout << *pIntArray << "\n";  
    pIntArray = pIntArray + 1;  
}  
```  
  
 Mimo że całkowitą wartość 1 jest dodawana do `pIntArray`, nie oznacza "Dodaj 1 adres"; zamiast oznacza "Dostosuj kursor do następnego obiektu w tablicy" jest 2 bajty (lub `sizeof( int )`) natychmiast.  
  
> [!NOTE]
>  Kod w postaci `pIntArray = pIntArray + 1` rzadko zostanie znaleziony w programach języka C++; przeprowadzić przyrostu te formularze są preferowane: `pIntArray++` lub `pIntArray += 1`.  
  
## <a name="pointer-subtraction"></a>Odejmowanie wskaźnika  
 Jeśli oba operandy są wskaźnikami, wynik odejmowania różni (w elementach tablicy) argumentów. Wyrażenie odejmowania daje podpisem całkowitego wynik o typie **ptrdiff_t —** (zdefiniowane w pliku standardowych dołączonych \<stddef.h >).  
  
 Jeden z argumentów może być typu całkowitego, tak długo, jak jest drugi argument operacji. Wynik odejmowania jest taki sam typ co oryginalny wskaźnik. Wartość odejmowania jest wskaźnikiem do (*n* - *i*) th elementu tablicy, której *n* jest element wskazywany przez oryginalny wskaźnik i *i* jest całkowitą wartość drugiego operandu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Dwuargumentowymi](../cpp/expressions-with-binary-operators.md)   
 [C++ wbudowane operatory, pierwszeństwo i kojarzenie](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory dodawania języka C](../c-language/c-additive-operators.md)
