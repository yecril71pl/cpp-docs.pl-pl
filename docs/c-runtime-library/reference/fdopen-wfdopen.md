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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 82a7e891e8bd6031ebbf761534b6df7cd8488d36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347388"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen, _wfdopen

Kojarzy strumień z plikiem, który został wcześniej otwarty dla niskiego poziomu we/wy.

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

*Fd*<br/>
Deskryptor pliku otwartego pliku.

*Tryb*<br/>
Typ dostępu do plików.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do otwartego strumienia. Wartość wskaźnika zerowego wskazuje błąd. Gdy wystąpi błąd, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [obszarze Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EBADF**, co wskazuje na zły deskryptor pliku lub **EINVAL**, który wskazuje, że *tryb* był wskaźnikiem null.

Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_fdopen** kojarzy strumień we/wy z plikiem identyfikowanym przez *fd*i w ten sposób umożliwia buforowanie i sformatowanie pliku otwieranego dla niskiego poziomu we/wy. **_wfdopen** jest szerokoznakową wersją **_fdopen**; argument *mode* do **_wfdopen** jest ciągiem znaków o szerokim charakterze. **_wfdopen** i **_fdopen** w przeciwnym razie zachowują się identycznie.

Deskryptory plików przekazywane do **_fdopen** są własnością zwróconego **strumienia &#42;pliku.** Jeśli **_fdopen** się powiedzie, nie należy wywoływać [ \_zamknięcia](close.md) deskryptora pliku. Wywołanie [fclose](fclose-fcloseall.md) na zwrócony **plik &#42;** również zamyka deskryptora pliku.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|\_Unicode \_i MBCS nie zdefiniowane|\_Definicja MBCS|\_Zdefiniowano UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

Ciąg znaków *trybu* określa typ dostępu do pliku żądanego dla pliku:

| *Tryb* | Dostęp |
|--------|--------|
| **"r"** | Otwiera się do czytania. Jeśli plik nie istnieje lub nie można go odnaleźć, **wywołanie fopen** nie powiedzie się. |
| **"w"** | Otwiera pusty plik do zapisania. Jeśli dany plik istnieje, jego zawartość zostanie zniszczona. |
| **"a"** | Otwiera się do zapisu na końcu pliku (dołączanie). Tworzy plik, jeśli nie istnieje. |
| **"r+"** | Otwiera się zarówno do czytania, jak i pisania. Plik musi istnieć. |
| **"w+"** | Otwiera pusty plik do odczytu i zapisu. Jeśli plik istnieje, jego zawartość zostanie zniszczona. |
| **"a+"** | Otwiera do czytania i dołączania. Tworzy plik, jeśli nie istnieje. |

Po otwarciu pliku z typem dostępu **"a"** lub **"a+",** wszystkie operacje zapisu występują na końcu pliku. Wskaźnik pliku można zmienić położenie za pomocą [fseek](fseek-fseeki64.md) lub [przewijania](rewind.md)do tyłu , ale jest zawsze przenoszony z powrotem na koniec pliku przed przeprowadzeniem jakiejkolwiek operacji zapisu. W związku z tym istniejące dane nie mogą być zastąpione. Po określeniu typu dostępu **"r+",** **"w+"** lub **"a+"** dozwolone jest zarówno odczyt, jak i zapis (mówi się, że plik jest otwarty dla "aktualizacji"). Jednak po przełączeniu między czytaniem a zapisem musi nastąpić interwencja [fflush](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)lub [operacji przewijania do tyłu.](rewind.md) Można określić bieżącą pozycję dla operacji [fsetpos](fsetpos.md) lub [fseek,](fseek-fseeki64.md) jeśli chcesz.

Oprócz powyższych wartości, w *trybie* można również uwzględnić następujące znaki, aby określić tryb tłumaczenia dla znaków nowego rzędu:

| modyfikator *trybu* | Zachowanie |
|-----------------|----------|
| **t** | Otwórz w trybie tekstowym (przetłumaczonym). W tym trybie kombinacje kanału informacyjnego wiersza powrotu karetki (CR-LF) są tłumaczone na jednowierszowe kanały informacyjne (LF) na wejściu, a znaki LF są tłumaczone na kombinacje CR-LF na wyjściu. Ponadto ctrl+Z jest interpretowany jako znak końca pliku na danych wejściowych. |
| **B** | Otwórz w trybie binarnym (nieprzetłumaczonym). Wszelkie tłumaczenia z trybu **t** są pomijane. |
| **C** | Włącz flagę zatwierdzania skojarzonej *nazwy pliku,* tak aby zawartość buforu plików była zapisywana bezpośrednio na dysku, jeśli wywoływana jest **nazwa fflush** lub **_flushall.** |
| **N** | Zresetuj flagę zatwierdzania skojarzonej *nazwy pliku* na "no-commit". Domyślnie włączone. Zastępuje również globalną flagę zatwierdzania, jeśli program zostanie powiązany z plikiem Commode.obj. Domyślna flaga zatwierdzania globalnego to "no-commit", chyba że program zostanie jawnie powiązany z plikiem Commode.obj. |

Opcje *trybu* **t**, **c**i **n** to rozszerzenia firmy Microsoft dla **fopen** i **_fdopen**. Nie używaj ich, jeśli chcesz zachować przenośność ANSI.

Jeśli **t** lub **b** nie jest podany w *trybie,* domyślny tryb tłumaczenia jest zdefiniowany przez zmienną [ \_](../../c-runtime-library/fmode.md)globalną fmode . Jeśli **argument jest** poprzedzony t lub **b,** funkcja kończy się niepowodzeniem i zwraca wartość NULL. Aby zapoznać się z omówieniami trybów tekstowych i binarnych, zobacz [We/Wy pliku w trybie tekstowym i binarnym](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Prawidłowe znaki dla ciągu *trybu* używanego w **fopen** i **_fdopen** odpowiadają argumentom *oflag używanym* w [ \_open](open-wopen.md) i [ \_sopen,](sopen-wsopen.md)jak pokazano w tej tabeli:

|Znaki w *ciągu trybu*|Równoważna wartość *oflag* dla **_open** i **_sopen**|
|---------------------------------|---------------------------------------------------|
|**A**|**\_O\_WRONLY &#124; \_O\_APPEND** (zwykle ** \_O\_WRONLY \_\_&#124; O CREAT \_\_&#124; O APPEND)**|
|**a+**|**\_O\_RDWR &#124; \_O\_APPEND** (zwykle ** \_O\_RDWR \_\_&#124; O APPEND \_\_&#124; O CREAT)**|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**W**|**\_O\_WRONLY** (zwykle ** \_O\_WRONLY \_\_&#124; O CREAT \_\_&#124; O TRUNC)**|
|**w+**|**\_O\_RDWR** (zwykle ** \_O\_RDWR \_\_&#124; O CREAT \_\_&#124; O TRUNC)**|
|**B**|**\_O\_BINARNY**|
|**t**|**\_O\_TEKST**|
|**C**|Brak|
|**N**|Brak|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_fdopentxt"></a>Dane wejściowe: crt_fdopen.txt

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
[\_dup, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_otwarte, \_wopen](open-wopen.md)<br/>
