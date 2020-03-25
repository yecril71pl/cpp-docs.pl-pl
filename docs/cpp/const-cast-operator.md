---
title: Operator const_cast
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: d2711142e4aa73cc0119949876e7e593067cd45d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180345"
---
# <a name="const_cast-operator"></a>Operator const_cast

Usuwa atrybuty **const**, **volatile**i **__unaligned** z klasy.

## <a name="syntax"></a>Składnia

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>Uwagi

Wskaźnik do dowolnego typu obiektu lub wskaźnika do składowej danych może być jawnie konwertowany na typ, który jest taki sam, z wyjątkiem kwalifikatorów **const**, **volatile**i **__unaligned** . W przypadku wskaźników i odwołań wynik będzie odnosił się do oryginalnego obiektu. W przypadku wskaźników do elementów członkowskich danych wynik będzie odwoływać się do tego samego elementu członkowskiego, co oryginalny wskaźnik (uncast) do elementu członkowskiego danych. W zależności od typu obiektu, do którego istnieje odwołanie, operacja zapisu za pomocą wskaźnika, odwołania lub wskaźnika do składowej danych może spowodować niezdefiniowane zachowanie.

Nie można użyć operatora **const_cast** , aby bezpośrednio przesłonić stałą wartość zmiennej stałej.

Operator **const_cast** konwertuje wartość wskaźnika o wartości null na wartość wskaźnika o wartości null typu docelowego.

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

W wierszu zawierającym **const_cast**typ danych **tego** wskaźnika jest `const CCTest *`. Operator **const_cast** zmienia typ **danych wskaźnika na** `CCTest *`, umożliwiając modyfikowanie `number` elementu członkowskiego. Rzutowanie jest przeznaczone tylko dla pozostałej części instrukcji, w której występuje.

## <a name="see-also"></a>Zobacz też

[Operatory rzutowania](../cpp/casting-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
