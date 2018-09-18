---
title: const_cast Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- const_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 314e8363fafa4f2a6649055f2c608cd5b7edd18c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070083"
---
# <a name="constcast-operator"></a>Operator const_cast

Usuwa **const**, **volatile**, i **__unaligned** atrybutów z klasy.

## <a name="syntax"></a>Składnia

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>Uwagi

Wskaźnik do dowolnego typu obiektu lub wskaźnika do składowej danych może być jawnie konwertowane na typ, który jest identyczny, z wyjątkiem **const**, **volatile**, i **__unaligned** Kwalifikatory. Wskaźniki i odwołania wynik będzie odnosił się do oryginalnego obiektu. Dla wskaźników do składowych danych wynik będzie odnosił się do tego samego elementu członkowskiego jako oryginalny wskaźnik (uncast), aby element członkowski danych. W zależności od typu przywoływanego obiektu niezdefiniowane zachowanie może powodować generowanie operacji zapisu za pośrednictwem wynikowego wskaźnika, odwołanie lub wskaźnik do składowej danych.

Nie można użyć **const_cast** operator bezpośrednio zastąpić stan stałej zmiennej stałej.

**Const_cast** operator konwertuje wartość pustego wskaźnika do wartości pustego wskaźnika typu miejsca docelowego.

## <a name="example"></a>Przykład

```cpp
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

Na wiersz zawierający **const_cast**, typ danych **to** wskaźnik jest `const CCTest *`. **Const_cast** operator zmienia typu danych **to** wskaźnik do `CCTest *`, dzięki czemu element członkowski `number` do zmodyfikowania. Rzutowanie jest ważny tylko dla pozostałych instrukcji, w której występuje.

## <a name="see-also"></a>Zobacz także

[Operatory rzutowania](../cpp/casting-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)