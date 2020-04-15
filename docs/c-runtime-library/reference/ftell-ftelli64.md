---
title: ftell, _ftelli64
ms.date: 4/2/2020
api_name:
- _ftelli64
- ftell
- _o__ftelli64
- _o_ftell
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: bfe79610161a7f4032517d9f7eaa0de50be18e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345613"
---
# <a name="ftell-_ftelli64"></a>ftell, _ftelli64

Pobiera bieżącą pozycję wskaźnika pliku.

## <a name="syntax"></a>Składnia

```C
long ftell(
   FILE *stream
);
__int64 _ftelli64(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Strumienia*<br/>
Docelowa struktura **PLIKU.**

## <a name="return-value"></a>Wartość zwracana

**ftell** i **_ftelli64** zwracają bieżącą pozycję pliku. Wartość zwracana przez **ftell** i **_ftelli64** może nie odzwierciedlać fizycznego przesunięcia bajtów dla strumieni otwieranych w trybie tekstowym, ponieważ tryb tekstowy powoduje translację kanału informacyjnego wiersza powrotu karetki. Użyj **ftell** z [fseek](fseek-fseeki64.md) lub **_ftelli64** z [_fseeki64,](fseek-fseeki64.md) aby poprawnie powrócić do lokalizacji plików. W przypadku błędu **ftell** i **_ftelli64** wywołać nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje zwracają -1L i ustawić **errno** do jednej z dwóch stałych, zdefiniowane w ERRNO. H. Stała **EBADF** oznacza, że argument *strumienia* nie jest prawidłową wartością wskaźnika pliku lub nie odwołuje się do otwartego pliku. **EINVAL** oznacza nieprawidłowy argument *strumienia* został przekazany do funkcji. Na urządzeniach, których nie można szukać (takich jak terminale i drukarki) lub gdy *strumień* nie odwołuje się do otwartego pliku, zwracana wartość jest niezdefiniowana.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych.

## <a name="remarks"></a>Uwagi

Funkcje **ftell** i **_ftelli64** pobierają bieżącą pozycję wskaźnika pliku (jeśli istnieje) skojarzonego ze *strumieniem*. Położenie jest wyrażone jako przesunięcie względem początku strumienia.

Należy zauważyć, że po otwarciu pliku do dołączania danych bieżąca pozycja pliku jest określana przez ostatnią operację we/wy, a nie przez to, gdzie nastąpi następny zapis. Na przykład jeśli plik jest otwarty dla dodatku, a ostatnia operacja była odczytywana, pozycja pliku jest punktem, w którym rozpocznie się następna operacja odczytu, a nie miejscem rozpoczęcia następnego zapisu. (Po otwarciu pliku do dołączenia pozycja pliku jest przenoszona na koniec pliku przed jakąkolwiek operacją zapisu). Jeśli w pliku otwartym do dołączenia nie wystąpiła żadna operacja we/wy, pozycja pliku jest początkiem pliku.

W trybie tekstowym ctrl+Z jest interpretowany jako znak końca pliku na danych wejściowych. W plikach otwartych do odczytu / zapisu, **fopen** i wszystkie powiązane procedury sprawdzić CTRL + Z na końcu pliku i usunąć go, jeśli to możliwe. Odbywa się to, ponieważ za pomocą kombinacji **ftell** i [fseek](fseek-fseeki64.md) lub **_ftelli64** i [_fseeki64](fseek-fseeki64.md), aby przejść w pliku, który kończy się CTRL + Z może spowodować **ftell** lub **_ftelli64** zachowywać się nieprawidłowo pod koniec pliku.

Ta funkcja blokuje wątku wywołującego podczas wykonywania i dlatego jest bezpieczne dla wątków. Aby uzyskać wersję niezablokującą, zobacz **_ftell_nolock**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|----------------------|
|**ftell (ftell)**|\<stdio.h>|\<> errno.h|
|**_ftelli64**|\<stdio.h>|\<> errno.h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_ftell.c
// This program opens a file named CRT_FTELL.C
// for reading and tries to read 100 characters. It
// then uses ftell to determine the position of the
// file pointer and displays this position.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long position;
   char list[100];
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )
   {
      // Move the pointer by reading data:
      fread( list, sizeof( char ), 100, stream );
      // Get position after read:
      position = ftell( stream );
      printf( "Position after trying to read 100 bytes: %ld\n",
              position );
      fclose( stream );
   }
}
```

```Output
Position after trying to read 100 bytes: 100
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
