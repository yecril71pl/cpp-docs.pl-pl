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
ms.openlocfilehash: 4c516932eb8d50fb8c9fdbe6f8c48a3f590b1ffb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408487"
---
# <a name="setvbuf"></a>setvbuf

Buforowanie strumienia formantów i rozmiar buforu.

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

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

*buffer*<br/>
Bufor przydzielone przez użytkownika.

*Tryb*<br/>
Tryb buforowania.

*Rozmiar*<br/>
Rozmiar buforu w bajtach. Dopuszczalny zakres: 2 < = *rozmiar* < = int_max — (2147483647). Wewnętrznie, wartość podana dla *rozmiar* jest zaokrąglana do najbliższej wielokrotności 2.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0 w przypadku powodzenia.

Jeśli *strumienia* jest **NULL**, lub jeśli *tryb* lub *rozmiar* jest w nieprawidłowa zmiana, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca wartość -1 i zestawy **errno** do **einval —**.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Setvbuf —** funkcja pozwala programowi na sterowanie zarówno buforowanie i rozmiar dla buforu *strumienia*. *strumień* musi odwoływać się do otwartego pliku, która nie została poddana operacji We/Wy, ponieważ zostało otwarte. Tablica wskazywana przez *buforu* pełni rolę bufora, chyba że jest **NULL**, w którym to przypadku **setvbuf —** używa automatycznie przydzielonego buforu o długości  *rozmiar*/2 * 2 bajtów.

Tryb musi być **_iofbf —**, **_iolbf —**, lub **_ionbf —**. Jeśli *tryb* jest **_iofbf —** lub **_iolbf —**, następnie *rozmiar* jest używany jako rozmiar buforu. Jeśli *tryb* jest **_ionbf —**, strumień jest Niebuforowane i *rozmiar* i *buforu* są ignorowane. Wartości *tryb* i ich znaczenie:

|*tryb* wartość|Znaczenie|
|-|-|
**_IOFBF —**|Pełne buforowanie; oznacza to *buforu* jest używany jako bufor i *rozmiar* jest używany jako rozmiar buforu. Jeśli *buforu* jest **NULL**, automatycznie przydzielonego buforu *rozmiar* bajtów jest używany.
**_IOLBF —**|W niektórych systemach zapewnia buforowanie wiersza. Jednak systemu Win32, zachowanie jest taka sama jak **_iofbf —** — pełne buforowanie.
**_IONBF —**|Bufor nie jest używane, bez względu na to *buforu* lub *rozmiar*.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
