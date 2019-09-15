---
title: setvbuf
ms.date: 11/04/2016
api_name:
- setvbuf
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: 38b6474f550107a8edd941c7112ba98891ab3c12
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948181"
---
# <a name="setvbuf"></a>setvbuf

Steruje buforowaniem strumienia i rozmiarem buforu.

## <a name="syntax"></a>Składnia

```C
int setvbuf(
   FILE *stream,
   char *buffer,
   int mode,
   size_t size
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do struktury **pliku** .

*buffer*<br/>
Bufor przydzielony przez użytkownika.

*wyst*<br/>
Tryb buforowania.

*zmienia*<br/>
Rozmiar buforu w bajtach. Dozwolony zakres: 2 < = *size* < = INT_MAX (2147483647). Wewnętrznie wartość podana dla *rozmiaru* jest zaokrąglana w dół do najbliższej wielokrotności 2.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli powodzenie.

Jeśli *strumień* ma **wartość null**lub jeśli *tryb* lub *rozmiar* nie znajduje się w prawidłowej zmianie, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość-1 i ustawia **errno** na **EINVAL**.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **setvbuf —** pozwala programowi kontrolować zarówno buforowanie, jak i rozmiar buforu dla *strumienia*. *strumień* musi odwoływać się do otwartego pliku, który nie został poddany operacji we/wy, ponieważ został otwarty. Tablica wskazywana przez *bufor* jest używana jako bufor, chyba że ma **wartość null**, w takim przypadku **setvbuf —** używa automatycznie przydzielonego buforu *o długości lub*2 \* 2 bajtów.

Tryb musi mieć wartość **_IOFBF**, **_IOLBF**lub **_IONBF**. Jeśli *tryb* to **_IOFBF** lub **_IOLBF**, *rozmiar* jest używany jako rozmiar buforu. Jeśli *tryb* to **_IONBF**, strumień jest odbuforowany, a *rozmiar* i *bufor* są ignorowane. Wartości *trybu* i ich znaczenia są następujące:

|wartość *trybu*|Znaczenie|
|-|-|
| **_IOFBF** | Pełny buforowanie; oznacza to, że *bufor* jest używany jako bufor i *rozmiar* jest używany jako rozmiar buforu. Jeśli *bufor* ma **wartość null**, używana jest automatycznie przydzielony *rozmiar* bufora w bajtach. |
| **_IOLBF** | W przypadku niektórych systemów zapewnia to buforowanie wierszy. Jednak w przypadku systemu Win32 zachowanie jest takie samo jak **_IOFBF** — pełne buforowanie. |
| **_IONBF** | Nie jest używany żaden bufor, niezależnie od *buforu* lub *rozmiaru*. |

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_setvbuf.c
// This program opens two streams: stream1
// and stream2. It then uses setvbuf to give stream1 a
// user-defined buffer of 1024 bytes and stream2 no buffer.
//

#include <stdio.h>

int main( void )
{
   char buf[1024];
   FILE *stream1, *stream2;

   if( fopen_s( &stream1, "data1", "a" ) == 0 &&
       fopen_s( &stream2, "data2", "w" ) == 0 )
   {
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )
         printf( "Incorrect type or size of buffer for stream1\n" );
      else
         printf( "'stream1' now has a buffer of 1024 bytes\n" );
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )
         printf( "Incorrect type or size of buffer for stream2\n" );
      else
         printf( "'stream2' now has no buffer\n" );
      _fcloseall();
   }
}
```

```Output
'stream1' now has a buffer of 1024 bytes
'stream2' now has no buffer
```

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
