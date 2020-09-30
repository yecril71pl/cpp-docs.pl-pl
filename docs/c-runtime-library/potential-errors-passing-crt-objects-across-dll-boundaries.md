---
title: Potencjalne przekazywanie błędów obiektów CRT w poprzek granic DLL
description: Przegląd potencjalnych problemów, które mogą występować podczas przekazywania obiektów środowiska uruchomieniowego języka Microsoft C przez granicę biblioteki dołączanej dynamicznie (DLL).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: f6d831ac8b86be8a6669e8ee6c66da64507d129f
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590189"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>Potencjalne przekazywanie błędów obiektów CRT w poprzek granic DLL

Po przejściu obiektów środowiska uruchomieniowego w języku C (CRT), takich jak dojścia do plików, ustawienia regionalne i zmienne środowiskowe do lub z biblioteki DLL za pośrednictwem wywołań funkcji w granicach bibliotek DLL, może wystąpić nieoczekiwane zachowanie, jeśli biblioteka DLL lub wszystkie pliki, które są wywoływane do biblioteki DLL, używają różnych kopii bibliotek CRT.

Pokrewny problem może wystąpić w przypadku przydzielenia pamięci (jawnie za pomocą `new` lub `malloc` lub niejawnie z `strdup` , `strstreambuf::str` i tak dalej), a następnie przekazać wskaźnik na granicy biblioteki DLL, w której jest on zwolniony. Może to spowodować naruszenie dostępu do pamięci lub uszkodzenie sterty, jeśli biblioteka DLL i jej odbiorcy korzystają z różnych kopii bibliotek CRT.

Innym objawem tego problemu jest błąd w oknie danych wyjściowych podczas debugowania, takiego jak `HEAP[]: Invalid Address specified to RtlValidateHeap(#,#)`

## <a name="causes"></a>Przyczyny

Każda kopia biblioteki CRT ma oddzielny i odrębny stan, przechowywany w lokalnym magazynie wątków przez aplikację lub bibliotekę DLL.

Obiekty CRT, takie jak dojścia do plików, zmienne środowiskowe i ustawienia regionalne, są prawidłowe tylko dla kopii CRT w aplikacji lub bibliotece DLL, w której te obiekty zostały przydzieloną lub ustawione. Jeśli biblioteka DLL i jej klienci korzystają z różnych kopii biblioteki CRT, nie można przekazać tych obiektów CRT między granicami biblioteki DLL i oczekiwać ich użycia poprawnie po drugiej stronie. Jest to prawdą wersjami CRT przed uniwersalnym CRT w programie Visual Studio 2015 i nowszych.

Dla każdej wersji programu Visual Studio skompilowanej z Visual Studio 2013 lub wcześniejszą dostępna jest Biblioteka CRT o określonej wersji. Wewnętrzne szczegóły implementacji CRT, takie jak struktury danych i konwencje nazewnictwa, różnią się w każdej wersji. Dynamiczne łączenie kodu skompilowanego dla jednej wersji CRT z inną wersją biblioteki CRT nie było już obsługiwane. Czasami może to być spowodowane tym, że z powodu zbyt wielu zadań.

Ponieważ każda kopia biblioteki CRT ma swój własny Menedżer sterty, przydzielanie pamięci w jednej bibliotece CRT i przekazanie wskaźnika przez granicę biblioteki DLL w celu zwolnienia przez inną kopię biblioteki CRT, może spowodować uszkodzenie sterty. W przypadku projektowania biblioteki DLL w taki sposób, aby przekazywać obiekty CRT między granicami biblioteki DLL, lub przydzielać pamięć i oczekiwać, że zostanie ona zwolniona poza biblioteką DLL, klienci biblioteki DLL muszą używać tej samej kopii biblioteki CRT co Biblioteka DLL.

Biblioteka DLL i jej klienci zwykle używają tej samej kopii biblioteki CRT tylko wtedy, gdy oba są połączone w czasie ładowania do tej samej wersji biblioteki DLL CRT. Ponieważ wersja biblioteki uniwersalnej biblioteki CRT używanej przez program Visual Studio 2015 lub nowsza w systemie Windows 10 jest teraz centralnie wdrożonym składnikiem systemu Windows (ucrtbase.dll), jest to taka sama dla aplikacji skompilowanych w programie Visual Studio 2015 i nowszych wersjach. Jednak nawet gdy kod CRT jest identyczny, nie można przyznać pamięci przystosowanej w jednej stercie do składnika korzystającego z innego stosu.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W tym przykładzie przekazywana jest obsługa plików przez granicę biblioteki DLL.

Pliki DLL i exe są kompilowane przy użyciu programu `/MD` , dzięki czemu mają jedną kopię CRT.

W przypadku odbudowania z programem, `/MT` tak aby korzystały z oddzielnych kopii CRT, uruchomienie wynikowego **test1Main.exe** powoduje naruszenie zasad dostępu.

```cpp
// test1Dll.cpp
// compile with: cl /EHsc /W4 /MD /LD test1Dll.cpp
#include <stdio.h>
__declspec(dllexport) void writeFile(FILE *stream)
{
   char   s[] = "this is a string\n";
   fprintf( stream, "%s", s );
   fclose( stream );
}
```

```cpp
// test1Main.cpp
// compile with: cl /EHsc /W4 /MD test1Main.cpp test1Dll.lib
#include <stdio.h>
#include <process.h>
void writeFile(FILE *stream);

int main(void)
{
   FILE  * stream;
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );
   writeFile(stream);
   system( "type fprintf.out" );
}
```

```Output
this is a string
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Ten przykład przekazuje zmienne środowiskowe między granicami biblioteki DLL.

```cpp
// test2Dll.cpp
// compile with: cl /EHsc /W4 /MT /LD test2Dll.cpp
#include <stdio.h>
#include <stdlib.h>

__declspec(dllexport) void readEnv()
{
   char *libvar;
   size_t libvarsize;

   /* Get the value of the MYLIB environment variable. */
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );

   if( libvar != NULL )
      printf( "New MYLIB variable is: %s\n", libvar);
   else
      printf( "MYLIB has not been set.\n");
   free( libvar );
}
```

```cpp
// test2Main.cpp
// compile with: cl /EHsc /W4 /MT test2Main.cpp test2dll.lib
#include <stdlib.h>
#include <stdio.h>

void readEnv();

int main( void )
{
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );
   readEnv();
}
```

```Output
MYLIB has not been set.
```

Jeśli zarówno plik DLL, jak i exe są kompilowane przy użyciu `/MD` tak, aby była używana tylko jedna kopia CRT, program zostanie uruchomiony pomyślnie i wygeneruje następujące dane wyjściowe:

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Zobacz też

[Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
