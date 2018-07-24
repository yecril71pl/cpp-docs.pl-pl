---
title: setvbuf — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- setvbuf
apilocation:
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
apitype: DLLExport
f1_keywords:
- setvbuf
dev_langs:
- C++
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 279fb5f7c400a3c7160a9dc66c6cfce7ccaf2bc4
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208500"
---
# <a name="setvbuf"></a>setvbuf

Kontroluje buforowanie strumienia i rozmiar buforu.

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

*Stream*<br/>
Wskaźnik do **pliku** struktury.

*buffer*<br/>
Bufor przydzielony przez użytkownika.

*Tryb*<br/>
Tryb buforowania.

*Rozmiar*<br/>
Rozmiar buforu w bajtach. Dozwolony zakres: 2 < = *rozmiar* < = INT_MAX (2147483647). Wewnętrznie, wartość podana dla *rozmiar* jest zaokrąglana do najbliższej wielokrotności 2.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli kończy się pomyślnie.

Jeśli *strumienia* jest **NULL**, lub jeśli *tryb* lub *rozmiar* jest poza prawidłowe zmianę, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja zwraca wartość -1 i ustawia **errno** do **EINVAL**.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Setvbuf —** funkcja pozwala programowi na kontrolowanie zarówno buforowanie i rozmiar buforu *strumienia*. *strumień* musi odwoływać się do otwartego pliku, które nie zostało poddane operacji We/Wy, ponieważ zostało otwarte. Tablica wskazywany przez *buforu* służy jako bufor, chyba że jest to **NULL**, w którym to przypadku **setvbuf —** używa automatycznie przydzielonego buforu o długości  *rozmiar*/2 \* 2 bajty.

Tryb musi mieć wartość **_IOFBF**, **_IOLBF**, lub **_IONBF**. Jeśli *tryb* jest **_IOFBF** lub **_IOLBF**, następnie *rozmiar* jest używany jako rozmiar buforu. Jeśli *tryb* jest **_IONBF**, strumień jest Niebuforowane i *rozmiar* i *buforu* są ignorowane. Wartości *tryb* i ich znaczenie:

|*tryb* wartość|Znaczenie|
|-|-|
**_IOFBF**|Pełne buforowanie; oznacza to, że *buforu* służy jako bufor i *rozmiar* jest używany jako rozmiar buforu. Jeśli *buforu* jest **NULL**, automatycznie przydzielonego buforu *rozmiar* bajtów jest używany.
**_IOLBF**|W przypadku niektórych systemów zapewnia buforowanie wiersza. Jednak dla Win32, zachowanie jest taka sama jak **_IOFBF** — pełna buforowania.
**_IONBF**|Bufor nie jest używane, niezależnie od tego, *buforu* lub *rozmiar*.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
