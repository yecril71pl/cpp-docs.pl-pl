---
title: Potencjalne przekazywanie błędów obiektów CRT poprzek granic DLL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b9bc03e0d69492f7e46165f6f754f4a4ca3625d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031913"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>Potencjalne przekazywanie błędów obiektów CRT w poprzek granic DLL

Jeśli przekazujesz C Run-time (CRT) obiektów takich jak dojścia do plików i ustawień regionalnych, zmienne środowiskowe do lub z biblioteki DLL (wywołania funkcji przez granicę biblioteki DLL), nieoczekiwane zachowanie może wystąpić, jeśli biblioteka DLL, a także plików, wywołanie do biblioteki DLL, należy użyć różnych kopii Biblioteki CRT.

Powiązane problem może wystąpić, gdy przydzielić pamięci (albo jawnie za pomocą `new` lub `malloc`, lub niejawnie, przy użyciu `strdup`, `strstreambuf::str`i tak dalej) i następnie przekazać wskaźnik granicę biblioteki DLL, która będzie zwolniona. Może to spowodować uszkodzenie pamięci dostępu lub przekroczeniach sterty, jeśli biblioteka DLL i jej użytkownikach, należy użyć różnych kopii biblioteki CRT.

Inny objawem tego problemu może być błąd w oknie danych wyjściowych podczas debugowania, takich jak:

[] STERTY: Nieprawidłowy adres określony do RtlValidateHeap(#,#)

## <a name="causes"></a>Powoduje, że

Każda kopia biblioteki CRT ma odrębne i niezależne Państwo przechowywane w pamięci lokalnej wątku przez Twoją aplikację lub bibliotekę DLL. W efekcie CRT obiekty, takie jak dojścia do plików, zmienne środowiskowe i ustawienia regionalne są prawidłowe dla kopii CRT w aplikacji lub biblioteki DLL, gdy te obiekty są przydzielone lub ustaw tylko. Korzystając z biblioteki DLL, a jego klientami aplikacji różnych kopii biblioteki CRT, nie można tych obiektów CRT na krzyż granic DLL i powinni zostać pobrana prawidłowo po drugiej stronie. Jest to szczególnie istotne, CRT wersji przed Universal CRT w programie Visual Studio 2015 i nowszych wersjach. Było specyficzny dla wersji biblioteki CRT dla każdej wersji programu Visual Studio skompilowane przy użyciu Visual C++ 2013 lub starszej. Szczegóły wewnętrznej implementacji CRT, na przykład jego struktur danych i konwencje nazewnictwa, różniły się w każdej wersji. Dynamiczne łączenie kodzie skompilowanym dla jednej wersji CRT na inną wersję biblioteki DLL CRT nigdy nie zostały obsługiwane, chociaż czasami działałyby, bardziej przez szczęścia niż zgodnie z projektem.

Ponadto ponieważ każda kopia biblioteki CRT ma swój własny Menedżer sterty, przydzielania pamięci w jednej bibliotece CRT i przekazywania wskaźnika granicy DLL ma zostać zwolniony przez inną kopię biblioteki CRT jest potencjalną przyczyną uszkodzenia sterty. Projektując biblioteki DLL, który przekazuje obiektów CRT przez granicę lub przydziela pamięć i musi on zostać uwolniona poza bibliotekę DLL, można ograniczyć klientów aplikacji biblioteki dll, aby użyć tej samej kopii biblioteki CRT jako biblioteki DLL. Biblioteki DLL, a jego klientami używać tej samej kopii biblioteki CRT tylko wtedy, gdy są połączone w czasie ładowania do tej samej wersji biblioteki DLL CRT. Ponieważ wersja DLL biblioteki Universal CRT, używane przez program Visual Studio 2015, a później na system Windows 10 jest teraz składnik Windows wdrożone centralnie ucrtbase.dll, jest taka sama dla aplikacji utworzonych za pomocą programu Visual Studio 2015 i nowszych wersjach. Jednak nawet wtedy, gdy kod CRT jest taka sama, nie przekazujesz przydzielonej pamięci w jednym sterty do składnika, który używa innego sterty.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W tym przykładzie przechodzi uchwyt pliku granicę biblioteki DLL.

Plik DLL i .exe są tworzone za pomocą / / MD, dzięki czemu mają jedną kopię CRT.

W przypadku należy ponownie za pomocą/MT tak, aby były używane oddzielne kopie CRT, uruchomiona wynikowy wyniki test1Main.exe powoduje naruszenie zasad dostępu.

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

Ten przykład przekazuje zmienne środowiskowe granicę biblioteki DLL.

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

Jeśli plik DLL i .exe są tworzone za pomocą/MD, dzięki czemu jest używana tylko jedna kopia CRT, program zostanie uruchomiony pomyślnie i generuje następujące wyniki:

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Zobacz też

[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)