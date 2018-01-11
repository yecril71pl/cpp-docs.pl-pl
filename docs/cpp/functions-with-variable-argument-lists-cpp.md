---
title: "Funkcje z listami zmiennych argumentów (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a2f22f24206a125f9575529a203e5433f1b825a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="functions-with-variable-argument-lists--c"></a>Funkcje z argumentem zmiennej listy (C++)
Deklaracje funkcji, w których ostatniego członka jest wielokropek (...) może potrwać zmienną liczbę argumentów. W takich przypadkach C++ zawiera tylko sprawdzanie jawnie zadeklarowana argumentów typu. Listy zmiennych argumentów można użyć, gdy trzeba tworzyć funkcję, co może różnić się ogólne, że nawet liczbę i typy argumentów. Rodziny funkcji jest przykład funkcji, które używają listy zmiennych argumentów. `printf` *listy argumentów — deklaracja*  
  
## <a name="functions-with-variable-arguments"></a>Funkcji ze zmiennymi argumentami  
 Aby uzyskać dostęp do argumentów po deklarowane, użyj makra zawarte w pliku dołączanego standardowe STDARG. H, zgodnie z poniższym opisem.  
  
 **Dotyczące firmy Microsoft**  
  
 Microsoft C++ pozwala wielokropka określony jako argument, jeśli wielokropek jest ostatni argument i wielokropek jest poprzedzony przecinkami. W związku z tym deklaracji `int Func( int i, ... );` jest dozwolony, ale `int Func( int i ... );` nie jest.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Deklaracja funkcję ze zmienną liczbą argumentów wymaga co najmniej jednego argumentu symbolu zastępczego, nawet jeśli nie jest używany. Jeśli ten argument zastępczy nie jest podany, brak nie można uzyskać dostępu do pozostałych argumentów.  
  
 Gdy argumenty typu `char` są przekazywane jako argumenty zmienne są konwertowane na typ `int`. Podobnie, jeśli argumenty typu **float** są przekazywane jako argumenty zmienne są konwertowane na typ **podwójne**. Argumenty inne typy są poddawane zwykle promocje typów całkowitych i zmiennoprzecinkowych. Zobacz [konwersje standardowe](standard-conversions.md) Aby uzyskać więcej informacji.  
  
 Funkcje, które wymagają zmiennej listy są zadeklarowane za pomocą wielokropek (...) na liście argumentów. Użyj typów i makra, które zostały opisane w STDARG. H dołączyć plik do dostępu do argumentów, które są przekazywane przez listy zmiennych. Aby uzyskać więcej informacji na temat makr, zobacz [va_arg, va_copy, va_end, va_start —](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). w dokumentacji dotyczącej biblioteki wykonawczej języka C.  
  
 W poniższym przykładzie pokazano, jak makra współdziała z typem (deklaracja w STDARG. H): 
  
```  
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
  
1.  Należy ustanowić znacznika listy jako zmienną typu `va_list` przed uzyskaniem dostępu do żadnych zmiennych argumentów. W poprzednim przykładzie, nosi nazwę znacznika `vl`.  
  
2.  Oddzielne argumenty są dostępne za pomocą `va_arg` makra. Należy wskazać `va_arg` makro typ argumentu pobrać tak, aby go przenieść poprawną liczbę bajtów ze stosu. Jeśli określono nieprawidłowy typ inny niż dostarczona przez program wywołujący do rozmiaru `va_arg`, są nieprzewidywalne wyniki.  
  
3.  Należy jawnie Rzutuj wynik metody uzyskać za pomocą `va_arg` makro do żądanego typu.  
  
 Należy wywołać makro o zakończeniu przetwarzania argument zmiennej.`va_end`