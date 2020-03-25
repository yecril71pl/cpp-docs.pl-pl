---
title: sizeof — operator
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: bc1165cf1df3933575013906d1b24673467f0b36
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178720"
---
# <a name="sizeof-operator"></a>sizeof — operator

Zwraca rozmiar operandu w odniesieniu do rozmiaru typu **char**.

> [!NOTE]
>  Aby uzyskać informacje na temat operatora `sizeof ...`, zobacz [wielokropek i szablony wariadyczne](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Składnia

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Uwagi

Wynik operatora **sizeof** jest typu `size_t`, który jest typem całkowitym zdefiniowanym w pliku dołączanym \<STDDEF. h >. Ten operator pozwala uniknąć określania rozmiarów danych zależnych od maszyn w programach.

Argumentem operatora **sizeof** może być jeden z następujących:

- Nazwa typu. Aby użyć **operatora sizeof** z nazwą typu, nazwa musi być ujęta w nawiasy.

- Wyrażenie. W przypadku użycia z wyrażeniem **sizeof** może być określony z lub bez nawiasów. Wyrażenie nie jest oceniane.

Gdy operator **sizeof** jest stosowany do obiektu typu **char**, daje 1. Gdy operator **sizeof** jest stosowany do tablicy, daje całkowitą liczbę bajtów w tej tablicy, a nie rozmiar wskaźnika reprezentowanego przez identyfikator tablicy. Aby uzyskać rozmiar wskaźnika reprezentowanego przez identyfikator tablicy, przekaż go jako parametr do funkcji, która używa **operatora sizeof**. Na przykład:

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

Gdy operator **sizeof** zostanie zastosowany do typu **klasy**, **struktury**lub **Unii** , wynik jest liczbą bajtów w obiekcie tego typu oraz dopełnieniem dodanym do dopasowania elementów członkowskich na granicach wyrazów. Wynik nie musi być zgodny z rozmiarem obliczanym przez dodanie wymagań magazynu poszczególnych członków. Opcja kompilatora [/ZP](../build/reference/zp-struct-member-alignment.md) i dyrektywy pragma [Pack](../preprocessor/pack.md) wpływają na granice wyrównania dla elementów członkowskich.

Operator **sizeof** nigdy nie zwraca 0 nawet dla pustej klasy.

Operatora **sizeof** nie można używać z następującymi argumentami operacji:

- Obowiązki. (Jednak **sizeof** można zastosować do wskaźników do funkcji).

- Pola bitowe.

- Niezdefiniowane klasy.

- Typ **void**.

- Dynamicznie przydzielane tablice.

- Tablice zewnętrzne.

- Niekompletne typy.

- Nazwy z nawiasami niekompletnymi typów.

Gdy operator **sizeof** zostanie zastosowany do odwołania, wynik jest taki sam, jak w przypadku zastosowania operatora **sizeof** do samego obiektu.

Jeśli tablica niesizeowa jest ostatnim elementem struktury, operator **sizeof** zwraca rozmiar struktury bez tablicy.

Operator **sizeof** jest często używany do obliczania liczby elementów w tablicy przy użyciu wyrażenia w postaci:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Zobacz też

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
