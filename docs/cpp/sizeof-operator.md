---
title: sizeof — operator
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: c9ae581b1b3bea522f2c1557b8be44ee1f32eef1
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032294"
---
# <a name="sizeof-operator"></a>sizeof — operator

Daje rozmiar jego operand w odniesieniu do wielkości **typu char**.

> [!NOTE]
> Aby uzyskać `sizeof ...` informacje o operatorze, zobacz [Wielokropek i szablony variadic](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Składnia

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Uwagi

Wynik **sizeof** operatora jest typu `size_t`, typu całkowitego zdefiniowanego w pliku \<include stddef.h>. Ten operator pozwala uniknąć określania rozmiarów danych zależnych od komputera w programach.

Operand do **sizeof** może być jednym z następujących:

- Nazwa typu. Aby użyć **sizeof** z nazwą typu, nazwa musi być ujęta w nawiasy.

- Wyrażenie. W przypadku użycia z **wyrażeniem, sizeof** można określić z lub bez nawiasów. Wyrażenie nie jest oceniane.

Gdy **operator sizeof** jest stosowany do obiektu **typu char**, daje 1. Gdy **operator sizeof** jest stosowany do tablicy, daje całkowitą liczbę bajtów w tej tablicy, a nie rozmiar wskaźnika reprezentowanego przez identyfikator tablicy. Aby uzyskać rozmiar wskaźnika reprezentowanego przez identyfikator tablicy, przekaż go jako parametr do funkcji, która używa **sizeof**. Przykład:

## <a name="example"></a>Przykład

```cpp
#include <iostream>
using namespace std;

size_t getPtrSize( char *ptr )
{
   return sizeof( ptr );
}

int main()
{
   char szHello[] = "Hello, world!";

   cout  << "The size of a char is: "
         << sizeof( char )
         << "\nThe length of " << szHello << " is: "
         << sizeof szHello
         << "\nThe size of the pointer is "
         << getPtrSize( szHello ) << endl;
}
```

## <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
The size of a char is: 1
The length of Hello, world! is: 14
The size of the pointer is 4
```

Gdy **operator sizeof** jest stosowany do **klasy,** **struktury**lub typu **unii,** wynikiem jest liczba bajtów w obiekcie tego typu, plus wszelkie dopełnienie dodane do wyrównania elementów członkowskich w granicach wyrazu. Wynik nie musi odpowiadać rozmiarowi obliczonemu przez dodanie wymagań dotyczących magazynowania poszczególnych elementów członkowskich. Opcja kompilatora [/Zp](../build/reference/zp-struct-member-alignment.md) i [pragma pakietu](../preprocessor/pack.md) wpływają na granice wyrównania dla elementów członkowskich.

**Sizeof** operator nigdy nie daje 0, nawet dla pustej klasy.

Nie można używać operatora **sizeof** z następującymi operandami:

- Funkcje. (Jednak **sizeof** mogą być stosowane do wskaźników do funkcji.)

- Pola bitowe.

- Niezdefiniowane klasy.

- Typ **void**.

- Tablice przydzielane dynamicznie.

- Tablice zewnętrzne.

- Niekompletne typy.

- Nazwy niekompletnych typów w nawiasach.

Gdy **operator sizeof** jest stosowany do odwołania, wynik jest taki sam, jak gdyby **sizeof** zostały zastosowane do samego obiektu.

Jeśli tablica niewymiarowa jest ostatnim elementem struktury, **operator sizeof** zwraca rozmiar struktury bez tablicy.

Operator **sizeof** jest często używany do obliczania liczby elementów w tablicy przy użyciu wyrażenia formularza:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
