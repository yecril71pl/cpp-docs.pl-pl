---
title: Funkcje z listami zmiennych argumentów (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e66ee17f8aa82e46011a78e34baa79b3dea3cdb1
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947750"
---
# <a name="functions-with-variable-argument-lists--c"></a>Funkcje z zmiennej listami argumentów (C++)
Deklaracje funkcji, w których ostatniego członka jest może wielokropek (...) potrwać zmienną liczbę argumentów. W takich przypadkach C++ zapewnia kontrolę tylko w przypadku argumentów zadeklarowany w sposób jawny typów. Listy zmiennych argumentów można użyć, gdy należy wprowadzić funkcję, więc ogólne, że nawet liczbę i typy argumentów mogą się różnić. Rodziny funkcji jest przykładem funkcje korzystające z listy zmiennych argumentów. `printf` *lista deklaracji argumentów*  
  
## <a name="functions-with-variable-arguments"></a>Funkcje ze zmiennymi argumentami  
 Dostęp do argumentów po tych zadeklarowanych, użyj makra zawarte w pliku standardowych dołączonych \<stdarg.h > zgodnie z poniższym opisem.  
  
 **Microsoft Specific**  
  
 Microsoft C++ umożliwia z wielokropkiem, aby określić jako argument, gdy przycisk wielokropka jest ostatni argument i jest poprzedzony wielokropka, przecinkiem. Dlatego deklaracja `int Func( int i, ... );` jest dozwolony, ale `int Func( int i ... );` nie jest.  
  
 **END specyficzny dla Microsoft**  
  
 Deklaracja funkcji, która przyjmuje zmienną liczbę argumentów wymaga co najmniej jednego argumentu symbolu zastępczego, nawet jeśli nie jest używany. Jeśli ten argument zastępczy nie jest podany, nie ma możliwości dostępu pozostałe argumenty do.  
  
 Gdy argumentów typu **char** są przekazywane jako argumenty zmiennych są konwertowane na typ **int**. Podobnie, jeśli argumenty typu **float** są przekazywane jako argumenty zmiennych są konwertowane na typ **double**. Argumenty inne typy podlegają standardowym promocje typów całkowitych i zmiennoprzecinkowych. Zobacz [konwersje standardowe](standard-conversions.md) Aby uzyskać więcej informacji.  
  
 Funkcje, które wymagają listy zmiennych są zadeklarowane za pomocą wielokropek (...) na liście argumentów. Używać typów i makra, które są opisane w \<stdarg.h > Dołącz plik do argumentów dostępu, które są przekazywane przez listy zmiennych. Aby uzyskać więcej informacji na temat tych makr, zobacz [va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). w dokumentacji biblioteki wykonawczej C.  
  
 W poniższym przykładzie pokazano, jak makra współpracuje z typu (zadeklarowanych w \<stdarg.h >): 
  
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
  
 Poprzedni przykład ilustruje te ważne pojęcia:  
  
1.  Należy ustanowić znacznika listy jako zmienną typu `va_list` przed argumenty zmiennych są dostępne. W poprzednim przykładzie, nosi nazwę znacznika `vl`.  
  
2.  Oddzielne argumenty są dostępne przy użyciu `va_arg` makra. Musisz poinformować `va_arg` — makro typ argumentu do pobrania, aby go przenieść poprawną liczbę bajtów ze stosu. Jeśli określono nieprawidłowy typ o rozmiarze różni się od dostarczona przez program wywołujący do `va_arg`, wyniki są nieprzewidywalne.  
  
3.  Należy jawnie rzutowane wynik uzyskany przy użyciu `va_arg` makra do typu, który chcesz.  
  
 Musisz wywołać makra, aby zakończyć przetwarzanie argumentów zmiennej.`va_end`