---
title: 'Operatory przyrostka inkrementacji i dekrementacji: ++ i--| Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edfbb5076dfcbcbe511f8ec25c74f698cb82f33e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>Operatory przyrostka inkrementacji i dekrementacji: ++ i --
## <a name="syntax"></a>Składnia  
  
```  
postfix-expression ++  
postfix-expression --  
```  
  
## <a name="remarks"></a>Uwagi  
 Język C++ zawiera przedrostkowe i przyrostkowe operatory inkrementacyjne i dekrementacyjne; w tej sekcji opisano tylko przyrostkowe operatory inkrementacyjne i dekrementacyjne. (Aby uzyskać więcej informacji, zobacz [operatory prefiksów inkrementacji i dekrementacji](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md).) Jest to różnica między nimi w notacji przyrostkowego operatora występuje po *wyrażenie przyrostek*, w notacji prefiksów operator wydaje się przed *wyrażenia.* W poniższym przykładzie pokazano przyrostkowy operator inkrementacyjny:  
  
```  
i++;  
```  
  
 Efektem zastosowania przyrostkowego operatora inkrementacyjnego (`++`) jest zwiększenie wartości argumentu operacji o jedną jednostkę odpowiedniego typu. Podobnie, skutek stosowania przyrostek operator dekrementacji (**--**) to, że wartość argumentu jest o jedną jednostkę odpowiedniego typu.  
  
 Ważne jest, aby należy pamiętać, że przyrostek zwiększenie lub zmniejszenie wyrażenie ma wartość wyrażenia **przed** aplikacji odpowiednich operatora. Operacja zwiększania lub zmniejszania odbywa się **po** argument jest obliczane. Problem występuje tylko wtedy, gdy przyrostkowa operacja inkrementacyjna lub dekrementacyjna występuje w kontekście większego wyrażenia.  
  
 Po zastosowaniu przyrostkowego operatora do argumentu funkcji, nie ma gwarancji, że wartość zostanie zwiększona lub zmniejszona przed przekazaniem jej do funkcji.  Zobacz sekcję 1.9.17 w standardzie języka C++, aby uzyskać więcej informacji.  
  
 Zastosowanie operatora inkrementacji przyrostek do wskaźnika do tablicy obiektów typu **długi** faktycznie dodaje czterech do reprezentacji wewnętrznej wskaźnika. To działanie powoduje wskaźnika, które wcześniej określone *n*element th tablicy, aby odwołać się do (*n*+ 1) th element.  
  
 Argumenty operacji przyrostka inkrementacji i dekrementacji przyrostka musi być modyfikowalną (nie **const**) l wartości typu arytmetycznego lub wskaźnikowego. Typ wyniku jest taki sam, jak te *wyrażenie przyrostek*, ale nie jest już wartością l-value.  
  
**Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): argument operatory przyrostka inkrementacji lub dekrementacji operator nie może być typu `bool`.
  
 Poniższy kod ilustruje przyrostkowy operator inkrementacyjny:  
  
```  
// expre_Postfix_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 10;  
   cout << i++ << endl;  
   cout << i << endl;  
}  
```  
  
 Nie są obsługiwane operacje postinkrementacyjne i postdekrementacyjne na typach wyliczeniowych.  
  
```  
enum Compass { North, South, East, West );  
Compass myCompass;  
for( myCompass = North; myCompass != West; myCompass++ ) // Error  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia przyrostków](../cpp/postfix-expressions.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operatory przyrostka inkrementacji i dekrementacji języka C](../c-language/c-postfix-increment-and-decrement-operators.md)