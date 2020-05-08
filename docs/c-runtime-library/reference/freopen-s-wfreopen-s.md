---
title: freopen_s, _wfreopen_s
ms.date: 4/2/2020
api_name:
- _wfreopen_s
- freopen_s
- _o__wfreopen_s
- _o_freopen_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- freopen_s
- _tfreopen_s
- _wfreopen_s
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
ms.openlocfilehash: 9ccd2f52f8d746c3e555c9ad04fc6ae07c53a665
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915835"
---
# <a name="freopen_s-_wfreopen_s"></a>freopen_s, _wfreopen_s

Ponownie przypisuje wskaźnik pliku. Te wersje programu [freopen _wfreopen](freopen-wfreopen.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t freopen(
   FILE** pFile,
   const char *path,
   const char *mode,
   FILE *stream
);
errno_t _wfreopen(
   FILE** pFile,
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Wskaźnik do wskaźnika pliku, który ma zostać dostarczony przez wywołanie.

*ścieżka*<br/>
Ścieżka nowego pliku.

*wyst*<br/>
Dozwolony typ dostępu.

*produkcyjne*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca kod błędu. Jeśli wystąpi błąd, oryginalny plik zostanie zamknięty.

## <a name="remarks"></a>Uwagi

Funkcja **freopen_s** zamyka plik aktualnie skojarzony ze *strumieniem* i ponownie przypisze *strumień* do pliku określonego przez *ścieżkę*. **_wfreopen_s** to dwubajtowa wersja **_freopen_s**; argumenty *Path* i *mode* **_wfreopen_s** są ciągami znaków dwubajtowych. **_wfreopen_s** i **_freopen_s** zachowują się identycznie w inny sposób.

Jeśli którykolwiek z *pfile*, *Path*, *mode*lub *Stream* ma **wartość null**lub jeśli *ścieżka* jest pustym ciągiem, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i zwracają **EINVAL**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s** jest zwykle używany do przekierowywania wstępnie otwartych plików **stdin**, **stdout**i **stderr** do plików określonych przez użytkownika. Nowy plik skojarzony ze *strumieniem* jest otwarty z *trybem*, który jest ciągiem znaków określającym typ dostępu żądany dla pliku, w następujący sposób:

|*wyst*|Dostęp|
|-|-|
| **®** | Otwiera do odczytu. Jeśli plik nie istnieje lub nie można go znaleźć, wywołanie **freopen_s** nie powiedzie się. |
| **k** | Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona. |
| **z** | Otwiera do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF) przed zapisaniem nowych danych do pliku. Tworzy plik, jeśli nie istnieje. |
| **"r +"** | Otwiera zarówno do odczytu, jak i do zapisu. Plik musi istnieć. |
| **"w +"** | Otwiera pusty plik do odczytu i zapisu. Jeśli plik istnieje, jego zawartość zostaje zniszczona. |
| **"a +"** | Otwiera do odczytu i dołączania. Operacja dołączania obejmuje usunięcie znacznika EOF przed zapisaniem nowych danych w pliku. Znacznik EOF nie zostanie przywrócony po zakończeniu zapisywania. Tworzy plik, jeśli nie istnieje. |

Używaj typów **"w"** i **"w +"** z ostrożnością, ponieważ mogą one zniszczyć istniejące pliki.

Gdy plik jest otwierany z typem dostępu **"a"** lub **"a +"** , wszystkie operacje zapisu odbywają się na końcu pliku. Mimo że można zmienić położenie wskaźnika pliku przy użyciu [fseek](fseek-fseeki64.md) lub [przewijania do tyłu](rewind.md), wskaźnik pliku jest zawsze przenoszony z powrotem na koniec pliku przed przeprowadzeniem operacji zapisu. W rezultacie istniejące dane nie mogą być zastępowane.

Tryb **"a"** nie usuwa znacznika EOF przed dołączeniem do pliku. Po wystąpieniu operacji dołączania polecenie typu MS-DOS wyświetla tylko dane do oryginalnego znacznika EOF, a nie wszelkie dane dołączone do pliku. Tryb **"a +"** powoduje usunięcie znacznika EOF przed dołączeniem do pliku. Po dołączeniu, polecenie MS-DOS TYPE wyświetla wszystkie dane w pliku. Tryb **"a +"** jest wymagany do dołączania do pliku strumienia, który jest zakończony przy użyciu znacznika z oznaczeniem EOF Ctrl + z.

W przypadku określenia typu dostępu **"r +"**, **"z +"** lub **"a +** " są dozwolone operacje odczytu i zapisu (plik zostanie otwarty dla "Update"). Jednak podczas przełączania się między operacjami odczytu i zapisu musi istnieć interwencja [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)lub do [tyłu](rewind.md) . W razie potrzeby można określić bieżącą pozycję dla operacji [fsetpos](fsetpos.md) lub [fseek](fseek-fseeki64.md) . Oprócz powyższych wartości jeden z następujących znaków może być uwzględniony w ciągu *trybu* , aby określić tryb tłumaczenia dla nowych wierszy.

|modyfikator *trybu*|Tryb tłumaczenia|
|-|-|
| **&** | Otwórz w trybie tekst (przetłumaczony). |
| **b** | Otwórz w trybie binarnym (nieprzetłumaczony); Tłumaczenia obejmujące znaki powrotu karetki i wysuwu wiersza są pomijane. |

W trybie tekstu (tłumaczone) kombinacje wysuwu wiersza (CR-LF) są tłumaczone na znaki wysuwu wiersza (LF) na wejściu; Znaki LF są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W przypadku plików otwartych do odczytu lub zapisu z **"a +"** Biblioteka wykonawcza sprawdza, czy Ctrl + Z na końcu pliku i usuwa go, jeśli jest to możliwe. Dzieje się tak, ponieważ użycie [fseek](fseek-fseeki64.md) i [ftell](ftell-ftelli64.md) do przenoszenia w pliku może spowodować, że [fseek](fseek-fseeki64.md) zachowywać się niewłaściwie blisko końca pliku. Opcja **t** jest rozszerzeniem firmy Microsoft, które nie powinno być używane w przypadku, gdy wymagana jest przenośność ANSI.

Jeśli **t** lub **b** nie jest określony w *trybie*, domyślny tryb tłumaczenia jest definiowany przez zmienną globalną [_fmode](../../c-runtime-library/fmode.md). Jeśli **t** lub **b** jest poprzedzony argumentem, funkcja kończy się niepowodzeniem i zwraca **wartość null**.

Aby zapoznać się z omówieniem trybów tekstowych i binarnych, zobacz [plik tekstowy i tryb binarny we/wy](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**freopen_s**|\<stdio. h>|
|**_wfreopen_s**|\<stdio. h> lub \<WCHAR. h>|

Konsola nie jest obsługiwana w aplikacjach platforma uniwersalna systemu Windows (platformy UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane przed użyciem funkcji języka C w aplikacjach platformy UWP. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_freopen_s.c
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   errno_t err;
   // Reassign "stderr" to "freopen.out":
   err = freopen_s( &stream, "freopen.out", "w", stderr );

   if( err != 0 )
      fprintf( stdout, "error on freopen\n" );
   else
   {
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );
      fprintf( stream, "This will go to the file 'freopen.out'\n" );
      fclose( stream );
   }
   system( "type freopen.out" );
}
```

```Output
successfully reassigned
This will go to the file 'freopen.out'
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
