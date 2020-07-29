---
title: sizeof — operator
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: 13e181bf84e359d433fbe951b1aa69320a1f0013
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186298"
---
# <a name="sizeof-operator"></a>sizeof — operator

Zwraca rozmiar operandu w odniesieniu do rozmiaru typu **`char`** .

> [!NOTE]
> Aby uzyskać informacje na temat `sizeof ...` operatora, zobacz [wielokropek i szablony wariadyczne](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Składnia

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Uwagi

Wynik **`sizeof`** operatora jest typu `size_t` , który jest typem całkowitym zdefiniowanym w pliku dołączanym \<stddef.h> . Ten operator pozwala uniknąć określania rozmiarów danych zależnych od maszyn w programach.

Operandem **`sizeof`** może być jeden z następujących:

- Nazwa typu. Aby można było użyć nazwy **`sizeof`** typu, nazwa musi być ujęta w nawiasy.

- Wyrażenie. W przypadku użycia z wyrażeniem **`sizeof`** można określić z nawiasami lub bez nich. Wyrażenie nie jest oceniane.

Gdy **`sizeof`** operator jest stosowany do obiektu typu **`char`** , daje 1. Gdy **`sizeof`** operator jest stosowany do tablicy, daje całkowitą liczbę bajtów w tej tablicy, a nie rozmiar wskaźnika reprezentowanego przez identyfikator tablicy. Aby uzyskać rozmiar wskaźnika reprezentowanego przez identyfikator tablicy, przekaż go jako parametr do funkcji, która używa **`sizeof`** . Na przykład:

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

Gdy **`sizeof`** operator zostanie zastosowany do **`class`** typu, **`struct`** , lub **`union`** , wynik jest liczbą bajtów w obiekcie tego typu, a wszelkie dopełnienie dodane w celu dopasowania elementów członkowskich do granic wyrazów. Wynik nie musi być zgodny z rozmiarem obliczanym przez dodanie wymagań magazynu poszczególnych członków. Opcja kompilatora [/ZP](../build/reference/zp-struct-member-alignment.md) i dyrektywy pragma [Pack](../preprocessor/pack.md) wpływają na granice wyrównania dla elementów członkowskich.

**`sizeof`** Operator nigdy nie zwraca 0 nawet dla pustej klasy.

**`sizeof`** Nie można użyć operatora z następującymi argumentami operacji:

- Obowiązki. (Jednak **`sizeof`** można je zastosować do wskaźników do funkcji).

- Pola bitowe.

- Niezdefiniowane klasy.

- Typ **`void`** .

- Dynamicznie przydzielane tablice.

- Tablice zewnętrzne.

- Niekompletne typy.

- Nazwy z nawiasami niekompletnymi typów.

Gdy **`sizeof`** operator jest stosowany do odwołania, wynik jest taki sam, jak gdyby **`sizeof`** został on zastosowany do samego obiektu.

Jeśli tablica o niezmienionym rozmiarze jest ostatnim elementem struktury, **`sizeof`** operator zwraca rozmiar struktury bez tablicy.

**`sizeof`** Operator jest często używany do obliczania liczby elementów w tablicy przy użyciu wyrażenia w postaci:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
