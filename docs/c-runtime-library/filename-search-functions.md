---
title: Funkcje wyszukiwania nazw plików
ms.date: 11/04/2016
api_location:
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
helpviewer_keywords:
- file names [C++], searching for
- _find function
- wfind function
- find function
- _wfind function
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
ms.openlocfilehash: 331d43f3e3a88786f8dac0a6f609f988beea9dbb
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300314"
---
# <a name="filename-search-functions"></a>Funkcje wyszukiwania nazw plików

Te funkcje szukają i zamykają wyszukiwania pod kątem określonych nazw plików:

- [_findnext, _wfindnext](../c-runtime-library/reference/findnext-functions.md)

- [_findfirst, _wfindfirst](../c-runtime-library/reference/findfirst-functions.md)

- [_findclose](../c-runtime-library/reference/findclose.md)

## <a name="remarks"></a>Uwagi

Funkcja `_findfirst` zawiera informacje dotyczące pierwszego wystąpienia nazwy pliku, które pasują do pliku określonego w argumencie `filespec`. Można użyć w `filespec` dowolnej kombinacji symboli wieloznacznych, które są obsługiwane przez system operacyjny hosta.

Funkcje zwracają informacje o pliku w strukturze `_finddata_t`, która jest zdefiniowana w IO. h. Różne funkcje w rodzinie wykorzystują wiele odmian w strukturze `_finddata_t`. Podstawowa struktura `_finddata_t` obejmuje następujące elementy:

`unsigned attrib`<br/>
Atrybut pliku.

`time_t time_create`<br/>
Godzina utworzenia pliku (-1L dla systemów plików FAT). Ten czas jest przechowywany w formacie UTC. Aby przekonwertować na czas lokalny, użyj [localtime_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md).

`time_t time_access`<br/>
Godzina ostatniego dostępu do pliku (-1L dla systemów plików FAT). Ten czas jest przechowywany w formacie UTC. Aby przekonwertować na czas lokalny, użyj `localtime_s`.

`time_t time_write`<br/>
Godzina ostatniego zapisu w pliku. Ten czas jest przechowywany w formacie UTC. Aby przekonwertować na czas lokalny, użyj `localtime_s`.

`_fsize_t size`<br/>
Długość pliku w bajtach.

`char name`[`_MAX_PATH`] nazwa zakończyła się wartością null pliku lub katalogu, bez ścieżki.

W systemach plików, które nie obsługują czasów tworzenia i ostatniego dostępu pliku, takich jak system plików FAT, pola `time_create` i `time_access` są zawsze 1L.

`_MAX_PATH` jest zdefiniowany w STDLIB. h jako 260 bajtów.

Nie można określić atrybutów docelowych (takich jak `_A_RDONLY`), aby ograniczyć liczbę operacji znajdowania. Te atrybuty są zwracane w polu `attrib` struktury `_finddata_t` i mogą mieć następujące wartości (zdefiniowane we/wy. h). Użytkownicy nie powinni korzystać z tych samych wartości dla pola `attrib`.

`_A_ARCH`<br/>
Folderu. Ustawiaj za każdym razem, gdy plik zostanie zmieniony i wyczyszczony przez polecenie **Backup** . Wartość: 0x20.

`_A_HIDDEN`<br/>
Ukryty plik. Zwykle niewidoczny w przypadku polecenia DIR, o ile nie zostanie użyta opcja **/Ah** . Zwraca informacje o normalnych plikach i plikach, które mają ten atrybut. Wartość: 0x02.

`_A_NORMAL`<br/>
Typow. Plik nie ma ustawionych atrybutów i może być odczytywany lub zapisywana bez ograniczeń. Wartość: 0x00.

`_A_RDONLY`<br/>
Tylko do odczytu. Nie można otworzyć pliku do zapisu i nie można utworzyć pliku o tej samej nazwie. Wartość: 0x01.

`_A_SUBDIR`<br/>
Podkatalogu. Wartość: 0x10.

`_A_SYSTEM`<br/>
Plik systemowy. Zwykle niewidoczny dla polecenia **dir** , chyba że jest używana opcja **/a** lub **/a: S** . Wartość: 0x04.

`_findnext` odnajdzie następną nazwę (jeśli istnieje), która pasuje do argumentu `filespec` określonego we wcześniejszym wywołaniu do `_findfirst`. Argument `fileinfo` powinien wskazywać strukturę zainicjowaną przez poprzednie wywołanie do `_findfirst`. W przypadku znalezienia dopasowania zawartość struktury `fileinfo` zostanie zmieniona zgodnie z wcześniejszym opisem. W przeciwnym razie pozostaje niezmieniona. `_findclose` zamyka określony uchwyt wyszukiwania i zwalnia wszystkie skojarzone zasoby dla `_findfirst` i `_findnext`. Dojście zwrócone przez `_findfirst` lub `_findnext` muszą zostać najpierw przesłane do `_findclose`, przed operacjami modyfikacji, takimi jak usuwanie, można wykonać na katalogach, które tworzą ścieżki do nich przekazana.

Można zagnieżdżać funkcje `_find`. Na przykład, jeśli wywołanie `_findfirst` lub `_findnext` odnajdzie plik, który jest podkatalogiem, nowe wyszukiwanie można zainicjować przy użyciu innego wywołania do `_findfirst` lub `_findnext`.

`_wfindfirst` i `_wfindnext` są wersjami znaków dwubajtowych `_findfirst` i `_findnext`. Argument struktury wersji szerokich znaków ma `_wfinddata_t` typ danych, który jest zdefiniowany w IO. h i w WCHAR. h. Pola tego typu danych są takie same jak w przypadku typu danych `_finddata_t`, z tą różnicą, że w `_wfinddata_t` pole Nazwa jest typu `wchar_t` zamiast typu `char`. W przeciwnym razie `_wfindfirst` i `_wfindnext` zachowują się identycznie w `_findfirst` i `_findnext`.

`_findfirst` i `_findnext` używają typu czasu 64-bitowego. Jeśli musisz użyć starego typu czasu 32-bitowego, możesz zdefiniować `_USE_32BIT_TIME_T`. Wersje tych funkcji, które mają sufiks `32` w swoich nazwach używają 32-bitowego typu czasu, a te z sufiksem `64` używają typu czasu 64-bitowego.

Funkcje `_findfirst32i64`, `_findnext32i64`, `_wfindfirst32i64`i `_wfindnext32i64` zachowują się identycznie w wersji 32-bitowej typu czasu dla tych funkcji, z wyjątkiem tego, że używają i zwracają długość pliku 64-bitowego. Funkcje `_findfirst64i32`, `_findnext64i32`, `_wfindfirst64i32`i `_wfindnext64i32` używają typu czasu 64-bitowego, ale używają długości plików 32-bitowych. Te funkcje używają odpowiednich odmian typu `_finddata_t`, w których pola mają różne typy dla czasu i rozmiaru pliku.

`_finddata_t` to w rzeczywistości makro, którego wynikiem jest `_finddata64i32_t` (lub `_finddata32_t` Jeśli `_USE_32BIT_TIME_T` jest zdefiniowana). W poniższej tabeli zestawiono różnice w `_finddata_t`:

|Struktura|Typ czasu|Typ rozmiaru pliku|
|---------------|---------------|--------------------|
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|`__int64`|
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|`__int64`|
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|

`_fsize_t` jest `typedef` dla `unsigned long` (32 bitów).

## <a name="example"></a>Przykład

```c
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

## <a name="see-also"></a>Zobacz także

[Wywołania systemowe](../c-runtime-library/system-calls.md)
