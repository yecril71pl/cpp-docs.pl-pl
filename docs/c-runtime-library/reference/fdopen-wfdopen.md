---
title: _fdopen, _wfdopen
ms.date: 4/2/2020
api_name:
- _fdopen
- _wfdopen
- _o__fdopen
- _o__wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 227f9e31c689b0259c429e2ffd9fce074903bd71
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920174"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen, _wfdopen

Kojarzy strumień z plikiem, który został wcześniej otwarty dla operacji we/wy niskiego poziomu.

## <a name="syntax"></a>Składnia

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parametry

*proces*<br/>
Deskryptor pliku otwartego pliku.

*wyst*<br/>
Typ dostępu do pliku.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do otwartego strumienia. Wartość wskaźnika o wartości null wskazuje na błąd. W przypadku wystąpienia błędu zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EBADF**, która wskazuje zły deskryptor pliku lub **EINVAL**, co wskazuje, że ten *tryb* był wskaźnikiem o wartości null.

Aby uzyskać więcej informacji o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_fdopen** kojarzy strumień we/wy z plikiem, który jest identyfikowany przez *FD*, i w ten sposób zezwala na plik otwarty dla operacji we/wy niskiego poziomu, które mają być buforowane i sformatowane. **_wfdopen** to dwubajtowa wersja **_fdopen**; argument *trybu* do **_wfdopen** jest ciągiem znaków dwubajtowych. **_wfdopen** i **_fdopen** zachowują się identycznie.

Deskryptory plików przesłane do **_fdopen** są własnością zwróconego **&#42;pliku** strumienia. W przypadku pomyślnego **_fdopen** nie należy wywoływać metody [ \_Close](close.md) dla deskryptora pliku. Wywołanie [fclose](fclose-fcloseall.md) w zwróconym **pliku &#42;** również zamyka deskryptora pliku.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|\_Nie zdefiniowano znaków UNICODE i \_MBCS|\_MBCS zdefiniowany|\_Zdefiniowany UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

Ciąg znaków *trybu* określa typ żądanego dostępu do pliku:

| *wyst* | Dostęp |
|--------|--------|
| **®** | Otwiera do odczytu. Jeśli plik nie istnieje lub nie można go znaleźć, wywołanie **fopen** kończy się niepowodzeniem. |
| **k** | Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona. |
| **z** | Otwiera do zapisu na końcu pliku (dołączanie). Tworzy plik, jeśli nie istnieje. |
| **"r +"** | Otwiera zarówno do odczytu, jak i do zapisu. Plik musi istnieć. |
| **"w +"** | Otwiera pusty plik do odczytu i zapisu. Jeśli plik istnieje, jego zawartość zostaje zniszczona. |
| **"a +"** | Otwiera do odczytu i dołączania. Tworzy plik, jeśli nie istnieje. |

Gdy plik zostanie otwarty z typem dostępu **"a"** lub **"a +"** , wszystkie operacje zapisu są wykonywane na końcu pliku. Wskaźnik pliku można zmienić przy użyciu [fseek](fseek-fseeki64.md) lub [przewijania do tyłu](rewind.md), ale jest on zawsze przenoszony z powrotem do końca pliku przed przeprowadzeniem operacji zapisu. W rezultacie istniejące dane nie mogą być zastępowane. W przypadku określenia typu dostępu **"r +"**, **"z +"** lub **"a +** " są dozwolone operacje odczytu i zapisu (plik zostanie otwarty dla "Update"). Jednak podczas przełączania się między operacjami odczytu i zapisu musi istnieć [fflush](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)lub [przewijania do tyłu](rewind.md) . Jeśli chcesz, możesz określić bieżącą pozycję dla operacji [fsetpos](fsetpos.md) lub [fseek](fseek-fseeki64.md) .

Oprócz powyższych wartości, w *trybie* można również dołączać do trybu tłumaczenia dla znaków nowego wiersza:

| modyfikator *trybu* | Zachowanie |
|-----------------|----------|
| **&** | Otwórz w trybie tekst (przetłumaczony). W tym trybie kombinacje wysuwu wiersza (CR-LF) są tłumaczone na jednowierszowe kanały informacyjne (LF) na wejściu, a znaki LF są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto Ctrl + Z jest interpretowany jako znak końca pliku na wejściu. |
| **b** | Otwórz w trybie binarnym (nieprzetłumaczonym). Wszystkie tłumaczenia z trybu **t** są pomijane. |
| **s** | Włącz flagę zatwierdzania dla skojarzonej *nazwy pliku* , aby zawartość bufora plików była zapisywana bezpośrednio na dysk, jeśli zostanie wywołana **fflush** lub **_flushall** . |
| **Azotan** | Zresetuj flagę zatwierdzania dla skojarzonej *nazwy pliku* na wartość "No-Commit". Domyślnie włączone. Zastępuje ona również globalną flagę zatwierdzania w przypadku łączenia programu z towarami. obj. Globalna flaga zatwierdzania ma wartość "No-Commit", chyba że jawnie połączysz program z towarami. obj. |

Opcje *trybu* **t**, **c**i **n** to rozszerzenia Microsoft dla **fopen** i **_fdopen**. Nie należy używać ich, jeśli chcesz zachować możliwość przenoszenia ANSI.

Jeśli **t** lub **b** nie jest określony w *trybie*, domyślny tryb tłumaczenia jest definiowany przez zmienną [ \_](../../c-runtime-library/fmode.md)globalną Fmode. Jeśli **t** lub **b** jest poprzedzony argumentem, funkcja kończy się niepowodzeniem i zwraca wartość null. Aby zapoznać się z omówieniem trybów tekstowych i binarnych, zobacz [plik tekstowy i tryb binarny we/wy](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Prawidłowe znaki w ciągu *trybu* używane w **fopen** i **_fdopen** odpowiadają argumentom *Oflag* używanym w [ \_otwartych](open-wopen.md) i [ \_sopen](sopen-wsopen.md), jak pokazano w poniższej tabeli:

|Znaki w ciągu *trybu*|Równoważna wartość *Oflag* dla **_open** i **_sopen**|
|---------------------------------|---------------------------------------------------|
|**z**|**\_O\_WRONLY &#124; \_o\_dołączenie** (zazwyczaj ** \_O\_WRONLY &#124; \_o\_tworzenie &#124; \_o\_dołączeniu**)|
|**a +**|**\_O\_RDWR &#124; \_o\_dołączenie** (zazwyczaj ** \_O\_RDWR &#124; \_\_o \_dołączenie &#124; o\_** tworzenie)|
|**®**|**\_O\_RDONLY**|
|**Język r +**|**\_O\_RDWR**|
|**k**|**\_O\_WRONLY** (zazwyczaj ** \_o\_WRONLY &#124; \_o\_&#124; \_o\_TRUNC —**)|
|**w +**|**\_O\_RDWR** (zazwyczaj ** \_o\_RDWR &#124; \_o\_&#124; \_o\_TRUNC —**)|
|**b**|**\_O\_plik binarny**|
|**&**|**\_O\_tekst**|
|**s**|Brak|
|**Azotan**|Brak|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fdopen**|\<stdio. h>|
|**_wfdopen**|\<stdio. h> lub \<WCHAR. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crt_fdopentxt"></a>Dane wejściowe: crt_fdopen. txt

```Input
Line one
Line two
```

### <a name="output"></a>Dane wyjściowe

```Output
Lines in file: 2
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[\_DUP, \_dUP2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_Otwórz, \_wOpen](open-wopen.md)<br/>
