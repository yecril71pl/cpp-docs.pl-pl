---
title: Funkcje wyszukiwania nazwy pliku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- file names [C++], searching for
- _find function
- wfind function
- find function
- _wfind function
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec6479a4803d7c0ee623d8506bf0ee9f2d674d7c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063375"
---
# <a name="filename-search-functions"></a>Funkcje wyszukiwania nazwy pliku

Te funkcje wyszukiwania i zamknąć wyszukuje określony plik nazwy:

- [_findnext, _wfindnext —](../c-runtime-library/reference/findnext-functions.md)

- [_findfirst, _wfindfirst —](../c-runtime-library/reference/findfirst-functions.md)

- [_findclose](../c-runtime-library/reference/findclose.md)

## <a name="remarks"></a>Uwagi

`_findfirst` Funkcji zawiera informacje dotyczące pierwszego wystąpienia nazwy pliku, który pasuje do pliku określonego w `filespec` argumentu. Można użyć w `filespec` dowolną kombinację znaków symbolu wieloznacznego, który jest obsługiwany przez system operacyjny hosta.

Te funkcje zwracają informacje dotyczące plików w `_finddata_t` struktury, która jest zdefiniowana w IO.h. Różnych funkcji w rodzinie użyć wielu wariantów na `_finddata_t` struktury. Podstawowa `_finddata_t` struktura zawiera następujące elementy:

`unsigned attrib`<br/>
Atrybut pliku.

`time_t time_create`<br/>
Godzina utworzenia pliku (L-1 dla systemów plików FAT). Tym razem jest przechowywany w formacie UTC. Aby dokonać konwersji czasu lokalnego, należy użyć [localtime_s —](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md).

`time_t time_access`<br/>
Czas ostatniego dostępu do plików (L-1 dla systemów plików FAT). Tym razem jest przechowywany w formacie UTC. Aby dokonać konwersji czasu lokalnego, należy użyć `localtime_s`.

`time_t time_write`<br/>
Czas ostatniego zapisu do pliku. Tym razem jest przechowywany w formacie UTC. Aby dokonać konwersji czasu lokalnego, należy użyć `localtime_s`.

`_fsize_t size`<br/>
Długość pliku w bajtach.

`char name`[ `_MAX_PATH`] Nazwa dopasowanym pliku lub katalogu, bez ścieżki zakończony znakiem null.

W systemach plików, które nie obsługują tworzenia i czas ostatniego dostępu do pliku, takich jak FAT system `time_create` i `time_access` pola są zawsze L-1.

`_MAX_PATH` jest zdefiniowane w Stdlib.h jako 260 bajtów.

Nie można określić atrybuty docelowe (takie jak `_A_RDONLY`) aby ograniczyć operacji wyszukiwania. Te atrybuty są zwracane w `attrib` pole `_finddata_t` struktury i może mieć następujące wartości (zdefiniowaną w IO.h). Użytkownicy nie należy polegać na są tylko wartości możliwe `attrib` pola.

`_A_ARCH`<br/>
Archiwum. Ustaw zawsze wtedy, gdy plik jest zmienione i wyczyszczone **kopii zapasowej** polecenia. Wartość: 0x20.

`_A_HIDDEN`<br/>
Ukryty plik. Zazwyczaj występuje przy użyciu polecenia DIR, chyba że używasz **/AH** opcji. Zwraca informacje o plikach normalne i plików, które mają ten atrybut. Wartość: 0x02.

`_A_NORMAL`<br/>
Normalny. Plik nie ma inne atrybuty zestawu i można je odczytać lub zapisywane bez ograniczeń. Wartość: 0x00.

`_A_RDONLY`<br/>
Tylko do odczytu. Nie można otworzyć pliku do zapisu i nie można utworzyć pliku, który ma taką samą nazwę. Wartość: 0x01.

`_A_SUBDIR`<br/>
Podkatalog. Wartość: 0x10.

`_A_SYSTEM`<br/>
System plików. Nie są zwykle widoczne z **DIR** , chyba że polecenie **/A** lub **/A:S** jest używana opcja. Wartość: 0x04.

`_findnext` znajduje następnej nazwy, jeśli odpowiada `filespec` argumentu określonym w wcześniejszego wywołania funkcji `_findfirst`. `fileinfo` Argument powinien wskazywać struktury inicjowane przez poprzednie wywołanie `_findfirst`. Jeśli zostanie znalezione dopasowanie, `fileinfo` zawartość struktury są zmieniane, zgodnie z wcześniejszym opisem. W przeciwnym razie zostanie pozostawiony bez zmian. `_findclose` Zamyka uchwyt wyszukiwania i zwalnia wszystkie powiązane zasoby dla obu `_findfirst` i `_findnext`. Uchwyt zwracany przez `_findfirst` lub `_findnext` muszą najpierw zostać przekazane do `_findclose`, zanim operacji modyfikowania, takie jak usuwanie, mogą być wykonywane na katalogi, które tworzą ścieżki przekazany do nich.

Można zagnieżdżać `_find` funkcji. Na przykład, jeśli wywołanie `_findfirst` lub `_findnext` znajdzie plik który jest to podkatalog nowego wyszukiwania mogą być inicjowane z innym wywołaniu `_findfirst` lub `_findnext`.

`_wfindfirst` i `_wfindnext` są wersjami znaków dwubajtowych `_findfirst` i `_findnext`. Argument struktury z wersjami szerokich znaków ma `_wfinddata_t` typu danych, która jest zdefiniowana w IO.h i w Wchar.h. Pola tego typu danych są takie same, jak `_finddata_t` typu danych, chyba że w `_wfinddata_t` pole nazwy jest typu `wchar_t` zamiast typu `char`. W przeciwnym razie `_wfindfirst` i `_wfindnext` zachowują się identycznie do `_findfirst` i `_findnext`.

`_findfirst` i `_findnext` Użyj typów w czasie 64-bitowych. Jeśli musisz użyć typu stare time 32-bitowy, można zdefiniować `_USE_32BIT_TIME_T`. Wersje tych funkcji, które mają `32` sufiks nazwy korzystanie z typu time 32-bitowe i osobom `64` sufiksa używa typów w czasie 64-bitowych.

Funkcje `_findfirst32i64`, `_findnext32i64`, `_wfindfirst32i64`, i `_wfindnext32i64` również zachowują się identycznie jak typ czasu 32-bitowe wersje tych funkcji z wyjątkiem użyć i zwraca 64-bitowy plik długości. Funkcje `_findfirst64i32`, `_findnext64i32`, `_wfindfirst64i32`, i `_wfindnext64i32` Użyj typów w czasie 64-bitowych, ale używania 32-bitowy plik długości. Te funkcje używają odpowiednich zmian `_finddata_t` typu, w którym pola mają różne typy czasu i rozmiaru pliku.

`_finddata_t` to naprawdę makro, które daje w wyniku `_finddata64i32_t` (lub `_finddata32_t` Jeśli `_USE_32BIT_TIME_T` jest zdefiniowana). W poniższej tabeli podsumowano różnice w `_finddata_t`:

|Struktura|Typ czasu|Typ rozmiaru pliku|
|---------------|---------------|--------------------|
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|`__int64`|
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|`__int64`|
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|

`_fsize_t` jest `typedef` dla `unsigned long` (32-bitowy).

## <a name="example"></a>Przykład

```
// crt_find.c
// This program uses the 32-bit _find functions to print
// a list of all files (and their attributes) with a .C extension
// in the current directory.

#include <stdio.h>
#include <stdlib.h>
#include <io.h>
#include <time.h>

int main( void )
{
   struct _finddata_t c_file;
   intptr_t hFile;

   // Find first .c file in current directory
   if( (hFile = _findfirst( "*.c", &c_file )) == -1L )
      printf( "No *.c files in current directory!\n" );
   else
   {
      printf( "Listing of .c files\n\n" );
      printf( "RDO HID SYS ARC  FILE         DATE %25c SIZE\n", ' ' );
      printf( "--- --- --- ---  ----         ---- %25c ----\n", ' ' );
      do {
         char buffer[30];
         printf( ( c_file.attrib & _A_RDONLY ) ? " Y  " : " N  " );
         printf( ( c_file.attrib & _A_HIDDEN ) ? " Y  " : " N  " );
         printf( ( c_file.attrib & _A_SYSTEM ) ? " Y  " : " N  " );
         printf( ( c_file.attrib & _A_ARCH )   ? " Y  " : " N  " );
         ctime_s( buffer, _countof(buffer), &c_file.time_write );
         printf( " %-12s %.24s  %9ld\n",
            c_file.name, buffer, c_file.size );
      } while( _findnext( hFile, &c_file ) == 0 );
      _findclose( hFile );
   }
}
```

```Output
Listing of .c files

RDO HID SYS ARC  FILE         DATE                           SIZE
--- --- --- ---  ----         ----                           ----
N   N   N   Y   blah.c       Wed Feb 13 09:21:42 2002       1715
N   N   N   Y   test.c       Wed Feb 06 14:30:44 2002        312
```

## <a name="see-also"></a>Zobacz też

[Wywołania systemowe](../c-runtime-library/system-calls.md)