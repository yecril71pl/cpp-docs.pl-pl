---
title: "Potencjalne przekazywanie błędów obiektów CRT poprzek granic DLL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c5fa79de11c7c3a1526fc91361eecdc74f8bdcd7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>Potencjalne przekazywanie błędów obiektów CRT w poprzek granic DLL
Podczas przekazywania C Run-time (CRT) obiekty takie jak dojścia do plików, ustawień regionalnych i zmiennych środowiskowych do lub z biblioteki DLL (wywołania funkcji granicy biblioteki DLL), nieoczekiwane zachowanie może wystąpić, jeśli plik DLL, a także pliki wywołanie do biblioteki DLL, użyj innej kopii Bibliotek CRT.  
  
 Powiązane problem może wystąpić, gdy przydzielić pamięci (jawnie za pomocą `new` lub `malloc`, albo niejawnie `strdup`, `strstreambuf::str`i tak dalej), a następnie przekazać wskaźnika granicy DLL ma zostać zwolniony. Może to spowodować uszkodzenie pamięci dostępu naruszenie lub sterty różne kopie biblioteki CRT korzystania z biblioteki DLL i jej użytkowników.  
  
 Inny objawem tego problemu może być błąd w oknie danych wyjściowych podczas debugowania, takich jak:  
  
 [] STERTY: Nieprawidłowy adres określony do RtlValidateHeap(#,#)  
  
## <a name="causes"></a>Powoduje, że  
 Biblioteka CRT każdej kopii ma stan odrębną, przechowywane w lokalny magazyn wątków przez aplikację lub DLL. W efekcie CRT obiekty, takie jak dojścia do plików, zmienne środowiskowe i ustawienia regionalne są prawidłowe dla kopię CRT w aplikacji lub DLL, gdy te obiekty są przydzielone lub ustaw tylko. Użycie biblioteki DLL a jego klientami aplikacji różne kopie biblioteki CRT, nie można przekazać te obiekty CRT granicy biblioteki DLL i oczekiwaniom do pobrania prawidłowo po drugiej stronie. Jest to szczególnie istotne w wersji CRT przed Universal CRT w programie Visual Studio 2015 i nowszych. Wystąpił określonej wersji biblioteki CRT dla każdej wersji programu Visual Studio skompilowane przy użyciu programu Visual C++ 2013 lub starszej. Szczegóły implementacji wewnętrzny CRT, na przykład jego struktury danych i konwencje nazewnictwa były różne w każdej wersji. Dynamicznie łączenie kodu skompilowanego dla jednej wersji CRT inną wersję biblioteki DLL CRT nigdy nie został obsługiwane, ale czasami działałoby, więcej przez szczęścia niż zgodnie z projektem.  
  
 Ponieważ każda kopia biblioteki CRT ma własną menedżera sterty, przydzielania pamięci w jednej biblioteki CRT i przekazanie wskaźnika granicy DLL używanych przez inną kopię biblioteki CRT jest również przyczyną uszkodzenie sterty. Podczas projektowania biblioteki DLL, który przekazuje obiektów CRT granicy lub przydziela pamięć i oczekuje ma zostać zwolniony poza bibliotekę DLL, można ograniczyć klientów aplikacji DLL, aby użyć tej samej kopii biblioteki CRT jako biblioteki DLL. Biblioteka DLL i jej klientów używać tej samej kopii biblioteki CRT tylko wtedy, gdy są połączone w czasie ładowania do tej samej wersji biblioteki DLL CRT. Ponieważ wersja DLL biblioteki Universal CRT używany przez Visual Studio 2015, a później systemu Windows 10 jest teraz centralnie wdrożonej składnik systemu Windows, ucrtbase.dll, jest taka sama dla aplikacji skompilowanych za pomocą programu Visual Studio 2015 i nowszych wersjach. Jednak nawet wtedy, gdy kod CRT jest taki sam, nie można ręcznie wyłączyć w jednym sterty do składnika, który używa innego sterty przydzielonej pamięci.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W tym przykładzie przekazuje dojście do pliku DLL granicy.  
  
 Plik DLL i .exe są tworzone za / / MD, więc mają pojedynczej kopii CRT.  
  
 Jeśli należy odtworzyć z/MT, tak aby były używane osobne kopie CRT, uruchomione wynikowy wyniki test1Main.exe w naruszenia zasad dostępu.  
  
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
 W tym przykładzie przekazuje zmiennych środowiskowych granicy biblioteki DLL.  
  
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
  
 Jeśli plik DLL i .exe są tworzone za / / MD, dzięki czemu jest używana tylko jedna kopia CRT, program zostanie wykonane pomyślnie i następujących danych wyjściowych:  
  
```  
New MYLIB variable is: c:\mylib;c:\yourlib  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka CRT — funkcje](../c-runtime-library/crt-library-features.md)