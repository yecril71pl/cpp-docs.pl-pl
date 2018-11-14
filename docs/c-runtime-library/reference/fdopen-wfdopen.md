---
title: _fdopen, _wfdopen
ms.date: 12/12/2017
apiname:
- _fdopen
- _wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 0cde110bf1dd12c23a6b0b658809502743d9edd3
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327164"
---
# <a name="fdopen-wfdopen"></a>_fdopen, _wfdopen

Kojarzy strumienia z pliku, który był wcześniej otwarty dla niskiego poziomu we/wy.

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

*FD*<br/>
Deskryptor pliku otwartego pliku.

*Tryb*<br/>
Typ dostępu do plików.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do otwartego strumienia. Wartość null wskaźnika wskazuje na błąd. Po wystąpieniu błędu, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono opcję **EBADF**, co oznacza deskryptor pliku uszkodzonych lub **EINVAL**, który wskazuje, że *tryb*  był wskaźnikiem typu null.

Aby uzyskać więcej informacji na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Fdopen —** funkcja kojarzy strumień we/wy z pliku który jest identyfikowany przez *fd*i dlatego umożliwia pliku, który jest otwierany dla niskiego poziomu we/wy do buforowanego i sformatowany. **_wfdopen —** to wersja znaku dwubajtowego **_fdopen —**; *tryb* argument **_wfdopen —** jest ciągiem znaku dwubajtowego. **_wfdopen —** i **_fdopen —** w przeciwnym razie zachowują się identycznie.

Deskryptory przekazywane do pliku **_fdopen —** należą przez zwrócony **pliku &#42;**  strumienia. Jeśli **_fdopen —** zakończy się pomyślnie, nie należy wywoływać metody [ \_Zamknij](close.md) na deskryptor pliku. Wywoływanie [fclose —](fclose-fcloseall.md) na zwracanego **pliku &#42;**  również zamyka deskryptor pliku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|\_UNICODE i \_MBCS niezdefiniowana|\_MBCS zdefiniowany|\_Definicja UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen —**|**_fdopen**|**_fdopen**|**_wfdopen**|

*Tryb* ciąg znaków określa rodzaj dostępu do plików wnioskowany dla pliku:

| *Tryb* | Access |
|--------|--------|
| **"r"** | Otwiera do odczytu. Jeśli plik nie istnieje lub nie można odnaleźć **fopen —** wywołanie zakończy się niepowodzeniem. |
| **"w"** | Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona. |
| **""** | Zostanie otwarty do zapisu na końcu pliku (dołączanie). Tworzy plik, jeśli nie istnieje. |
| **"r +"** | Otwiera Odczyt i zapis. Plik musi istnieć. |
| **"w +"** | Otwiera pusty plik Odczyt i zapis. Jeśli plik istnieje, jego zawartość zostaje zniszczona. |
| **"+"** | Otwiera do odczytu i dołączania. Tworzy plik, jeśli nie istnieje. |

Po otwarciu pliku za pomocą **""** lub **"+"** uzyskiwać dostępu do typu, wszystkie operacje zapisu występują na końcu pliku. Wskaźnik pliku może być przeniesiony za pomocą [fseek](fseek-fseeki64.md) lub [rewind](rewind.md), ale on jest zawsze przenoszony z powrotem na koniec pliku przed wszelkie zapisu operacji jest przeprowadzane. W związku z tym nie można zastąpić istniejące dane. Gdy **"r +"**, **"w +"**, lub **"+"** jest określony typ dostępu, Odczyt i zapis są dozwolone (plik jest określany jako otwarty do "aktualizacji"). Jednak podczas przełączania się między Odczyt i zapis, musi istnieć interwencyjne [fflush —](fflush.md), [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), lub [rewind](rewind.md) Operacja. Można określić bieżące położenie [fsetpos](fsetpos.md) lub [fseek](fseek-fseeki64.md) operacji, jeśli chcesz.

Oprócz powyższych wartości następujące znaki mogą być zawarte w *tryb* określić tryb translacji znaków nowego wiersza:

| *tryb* modyfikator | Zachowanie |
|-----------------|----------|
| **t** | Otwórz w tekście (tłumaczonym) trybu. W tym trybie karetki kanał wiersza powrotu (CR-LF) kombinacji są tłumaczone na jeden wiersz źródła (LF) na dane wejściowe, a znaki wysuwu wiersza są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto Ctrl + Z jest interpretowany jako znak końca pliku na wejściu. |
| **b** | Otwórz w trybie binarnym (nieprzetłumaczonym). Wszelkie tłumaczeń z **t** tryb są pomijane. |
| **c** | Włącz flagę zatwierdzania dla skojarzonego *filename* tak, aby zawartość buforu pliku są zapisywane bezpośrednio na dysku, jeśli **fflush —** lub **_flushall —** jest wywoływana. |
| **N** | Resetowanie flagi zatwierdzenia dla skojarzonego *filename* do "no-commit". Domyślnie włączone. Zastępuje również globalną flagę zatwierdzania, jeśli łączysz się program jest połączony z plikiem Commode.obj. Domyślna globalnej flagi zatwierdzania to "no-commit", chyba że jawnie połączyć program jest połączony z plikiem Commode.obj. |

**t**, **c**, i **n** *tryb* opcje są rozszerzeniami firmy Microsoft dla **fopen —** i **_fdopen —**. Nie należy ich używać, jeśli chcesz zachować przenośność kodowania ANSI.

Jeśli **t** lub **b** nie jest podana w *tryb*, domyślny tryb translacji jest zdefiniowany przez zmienną globalną [ \_fmode —](../../c-runtime-library/fmode.md). Jeśli **t** lub **b** jest poprzedzana argumentowi funkcja kończy się niepowodzeniem i zwraca wartość NULL. Aby uzyskać informacje o trybach tekstowym i binarnym, zobacz [tekstowych i binarnych We/Wy trybu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Prawidłowe znaki *tryb* ciąg użyty w **fopen —** i **_fdopen —** odpowiadają *oflag* argumenty używane w [ \_Otwórz](open-wopen.md) i [ \_sopen —](sopen-wsopen.md), jak pokazano w poniższej tabeli:

|Znaki w *tryb* ciągu|Równoważne *oflag* wartość **_otwórz** i **_sopen**|
|---------------------------------|---------------------------------------------------|
|**a**|**\_O\_WRONLY &#124; \_O\_APPEND** (zazwyczaj  **\_O\_WRONLY &#124; \_O\_CREAT &#124; \_O \_APPEND**)|
|**+**|**\_O\_RDWR &#124; \_O\_APPEND** (zazwyczaj  **\_O\_RDWR &#124; \_O\_APPEND &#124; \_O\_ Utwórz** )|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (zazwyczaj  **\_O\_WRONLY &#124; \_O\_CREAT &#124; \_O\_TRUNC**)|
|**w +**|**\_O\_RDWR** (zazwyczaj  **\_O\_RDWR &#124; \_O\_CREAT &#124; \_O\_TRUNC**)|
|**b**|**\_O\_BINARY**|
|**t**|**\_O\_TEXT**|
|**c**|Brak|
|**N**|Brak|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

### <a name="input-crtfdopentxt"></a>Dane wejściowe: crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>Dane wyjściowe

```Output
Lines in file: 2
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[\_Dup, \_dup2 —](dup-dup2.md)<br/>
[fclose —, \_fcloseall —](fclose-fcloseall.md)<br/>
[fopen —, \_wfopen —](fopen-wfopen.md)<br/>
[freopen —, \_wfreopen —](freopen-wfreopen.md)<br/>
[\_Otwórz, \_wopen —](open-wopen.md)<br/>
