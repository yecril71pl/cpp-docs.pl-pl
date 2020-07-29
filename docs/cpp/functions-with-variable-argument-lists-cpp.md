---
title: Funkcje z listami zmiennych argumentów (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
ms.openlocfilehash: 99f1f5cec2350f99bf2993947870f25e357ffc23
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213427"
---
# <a name="functions-with-variable-argument-lists--c"></a>Funkcje z listami zmiennych argumentów (C++)

Deklaracje funkcji, w których ostatni element członkowski jest wielokropka (...), mogą przyjmować zmienną liczbę argumentów. W takich przypadkach język C++ zapewnia sprawdzanie typu tylko dla jawnie zadeklarowanych argumentów. Listy zmiennych argumentów można użyć, gdy trzeba wykonać funkcję tak, że nawet liczba i typy argumentów mogą się różnić. Rodzina funkcji to przykład funkcji, które używają list argumentów zmiennych. `printf` *argument-deklaracja-list*

## <a name="functions-with-variable-arguments"></a>Funkcje z zmiennymi argumentami

Aby uzyskać dostęp do argumentów po tych zadeklarowanych, użyj makr zawartych w standardowym pliku dołączanym, \<stdarg.h> zgodnie z poniższym opisem.

**Specyficzne dla firmy Microsoft**

Język Microsoft C++ umożliwia określenie wielokropka jako argumentu, jeśli wielokropek jest ostatnim argumentem, a wielokropek jest poprzedzony przecinkiem. W związku z tym deklaracja `int Func( int i, ... );` ma charakter prawny, ale `int Func( int i ... );` nie jest.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Deklaracja funkcji, która przyjmuje zmienną liczbę argumentów, wymaga co najmniej jednego argumentu symbolu zastępczego, nawet jeśli nie jest używana. Jeśli nie podano tego argumentu symbolu zastępczego, nie ma możliwości uzyskania dostępu do pozostałych argumentów.

Gdy argumenty typu **`char`** są przekazane jako argumenty zmiennych, są konwertowane na typ **`int`** . Podobnie, gdy argumenty typu **`float`** są przekazane jako argumenty zmiennych, są konwertowane na typ **`double`** . Argumenty innych typów podlegają zwykłym, całkowitym i przepływającym awansom. Zobacz [standardowe konwersje](standard-conversions.md) , aby uzyskać więcej informacji.

Funkcje, które wymagają list zmiennych, są deklarowane przy użyciu wielokropka (...) na liście argumentów. Użyj typów i makr, które są opisane w polu \<stdarg.h> Dołącz plik do dostępu do argumentów, które są przekazane przez listę zmiennych. Aby uzyskać więcej informacji na temat tych makr, zobacz [va_arg, va_copy, va_end va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). w dokumentacji biblioteki wykonawczej C.

Poniższy przykład pokazuje, jak makra współpracują ze sobą z typem (zadeklarowanym w \<stdarg.h> ):

```cpp
// variable_argument_lists.cpp
#include <stdio.h>
#include <stdarg.h>

//  Declaration, but not definition, of ShowVar.
void ShowVar( char *szTypes, ... );
int main() {
   ShowVar( "fcsi", 32.4f, 'a', "Test string", 4 );
}

//  ShowVar takes a format string of the form
//   "ifcs", where each character specifies the
//   type of the argument in that position.
//
//  i = int
//  f = float
//  c = char
//  s = string (char *)
//
//  Following the format specification is a variable
//  list of arguments. Each argument corresponds to
//  a format character in the format string to which
// the szTypes parameter points
void ShowVar( char *szTypes, ... ) {
   va_list vl;
   int i;

   //  szTypes is the last argument specified; you must access
   //  all others using the variable-argument macros.
   va_start( vl, szTypes );

   // Step through the list.
   for( i = 0; szTypes[i] != '\0'; ++i ) {
      union Printable_t {
         int     i;
         float   f;
         char    c;
         char   *s;
      } Printable;

      switch( szTypes[i] ) {   // Type to expect.
         case 'i':
            Printable.i = va_arg( vl, int );
            printf_s( "%i\n", Printable.i );
         break;

         case 'f':
             Printable.f = va_arg( vl, double );
             printf_s( "%f\n", Printable.f );
         break;

         case 'c':
             Printable.c = va_arg( vl, char );
             printf_s( "%c\n", Printable.c );
         break;

         case 's':
             Printable.s = va_arg( vl, char * );
             printf_s( "%s\n", Printable.s );
         break;

         default:
         break;
      }
   }
   va_end( vl );
}
//Output:
// 32.400002
// a
// Test string
```

W poprzednim przykładzie przedstawiono następujące ważne pojęcia:

1. `va_list`Przed uzyskaniem dostępu do dowolnych argumentów zmiennych należy ustanowić znacznik listy jako zmienną typu. W poprzednim przykładzie znacznik jest wywoływany `vl` .

1. Poszczególne argumenty są dostępne za pomocą `va_arg` makra. Musisz poinformować `va_arg` makro o typie argumentu do pobrania, aby można było przesłać poprawną liczbę bajtów ze stosu. W przypadku określenia nieprawidłowego typu rozmiaru innego niż dostarczony przez program wywołujący do `va_arg` , wyniki są nieprzewidywalne.

1. Należy jawnie rzutować wynik uzyskany przy użyciu `va_arg` makra na żądany typ.

Należy wywołać makro, aby przerwać przetwarzanie argumentów zmiennej.`va_end`
