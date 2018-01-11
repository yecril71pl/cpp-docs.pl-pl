---
title: const_cast Operator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: const_cast_cpp
dev_langs: C++
helpviewer_keywords: const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 79c4aa00038f2d4d7e5cc3d1c86d2e28c6d44229
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="constcast-operator"></a>Operator const_cast
Usuwa **const**, `volatile`, i **__unaligned** atrybutów z klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
const_cast <   
type-id  
 > (   
expression  
 )  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Wskaźnik do dowolnego typu obiektu lub wskaźnika do elementu członkowskiego danych można jawnie konwertować na typ, który jest identyczny z wyjątkiem **const**, `volatile`, i **__unaligned** kwalifikatorów. Wskaźniki i odwołań wynik będzie odnosić się do oryginalnego obiektu. Dla wskaźników do elementów członkowskich danych wynik będzie odnosić się do elementu członkowskiego jako oryginalnego (uncast) wskaźnik do elementu członkowskiego danych. W zależności od typu obiektu, do którego istnieje odwołanie operacja zapisu za pośrednictwem wynikowego wskaźnika, reference lub wskaźnik do elementu członkowskiego danych może je spowodować niezdefiniowane zachowanie.  
  
 Nie można użyć `const_cast` operatora, aby bezpośrednio zastąpić stan stałej zmiennej stałej.  
  
 `const_cast` Operator konwertuje wartość wskaźnika o wartości null na wartość pustego wskaźnika typu docelowego.  
  
## <a name="example"></a>Przykład  
  
```  
// expre_const_cast_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class CCTest {  
public:  
   void setNumber( int );  
   void printNumber() const;  
private:  
   int number;  
};  
  
void CCTest::setNumber( int num ) { number = num; }  
  
void CCTest::printNumber() const {  
   cout << "\nBefore: " << number;  
   const_cast< CCTest * >( this )->number--;  
   cout << "\nAfter: " << number;  
}  
  
int main() {  
   CCTest X;  
   X.setNumber( 8 );  
   X.printNumber();  
}  
```  
  
 Na wiersz zawierający `const_cast`, typ danych miary `this` wskaźnika jest `const CCTest *`. `const_cast` Operator zmienia typ danych `this` wskaźnik do `CCTest *`, dzięki czemu element członkowski `number` do zmodyfikowania. Rzutowanie ważny tylko w pozostałej części instrukcji, w której znajduje się.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory rzutowania](../cpp/casting-operators.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)