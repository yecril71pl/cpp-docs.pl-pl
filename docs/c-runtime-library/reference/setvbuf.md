---
title: setvbuf
ms.date: 4/2/2020
api_name:
- setvbuf
- _o_setvbuf
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
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: 203265a8dd85854bcedd737359b856fdc4cce04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316266"
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

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

*Buforu*<br/>
Bufor przydzielony przez użytkownika.

*Tryb*<br/>
Tryb buforowania.

*Rozmiar*<br/>
Rozmiar buforu w bajtach. Dopuszczalny zakres: 2 <= *rozmiar* <= INT_MAX (2147483647). Wewnętrznie wartość podana dla *rozmiaru* jest zaokrąglana w dół do najbliższej wielokrotności 2.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli zakończy się pomyślnie.

Jeśli *strumień* ma **wartość NULL**lub jeśli *tryb* lub *rozmiar* nie mieści się w prawidłowej zmianie, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, ta funkcja zwraca wartość -1 i ustawia **errno** na **EINVAL**.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **setvbuf** pozwala programowi kontrolować zarówno buforowanie, jak i rozmiar bufora dla *strumienia.* *stream* musi odnosić się do otwartego pliku, który nie został poddany operacji we/wy od momentu otwarcia. Tablica wskazywane przez *bufor* jest używana jako bufor, chyba że jest **null**, w którym to \* przypadku **setvbuf** używa automatycznie przydzielonego buforu *o rozmiarze*długości /2 2 bajtów.

Tryb musi być **_IOFBF,** **_IOLBF**lub **_IONBF**. Jeśli *tryb* jest **_IOFBF** lub **_IOLBF**, *rozmiar* jest używany jako rozmiar buforu. Jeśli *tryb* jest **_IONBF,** strumień jest niebuforowany, a *rozmiar* i *bufor* są ignorowane. Wartości *dla trybu* i ich znaczenia to:

|wartość *trybu*|Znaczenie|
|-|-|
| **_IOFBF** | Pełne buforowanie; oznacza to, że *bufor* jest używany jako bufor i *rozmiar* jest używany jako rozmiar buforu. Jeśli *bufor* ma **wartość NULL,** zostanie użyty automatycznie przydzielony *rozmiar* buforu o długości. |
| **_IOLBF** | W przypadku niektórych systemów zapewnia to buforowanie linii. Jednak dla Win32 zachowanie jest taka sama jak **_IOFBF** — pełne buforowanie. |
| **_IONBF** | Bufor nie jest używany, niezależnie od *bufora* lub *rozmiaru*. |

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
