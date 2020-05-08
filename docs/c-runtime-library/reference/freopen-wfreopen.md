---
title: freopen, _wfreopen
ms.date: 4/2/2020
api_name:
- freopen
- _wfreopen
- _o__wfreopen
- _o_freopen
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
- _wfreopen
- _tfreopen
- freopen
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
ms.openlocfilehash: 435211b246f9943588aeef2005e501a9eac59c6b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916344"
---
# <a name="freopen-_wfreopen"></a>freopen, _wfreopen

Ponownie przypisuje wskaźnik pliku. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [freopen_s, _wfreopen_s](freopen-s-wfreopen-s.md).

## <a name="syntax"></a>Składnia

```C
FILE *freopen(
   const char *path,
   const char *mode,
   FILE *stream
);
FILE *_wfreopen(
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*ścieżka*<br/>
Ścieżka nowego pliku.

*wyst*<br/>
Dozwolony typ dostępu.

*produkcyjne*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do nowo otwartego pliku. Jeśli wystąpi błąd, oryginalny plik zostanie zamknięty, a funkcja zwróci wartość wskaźnika o **wartości null** . Jeśli *ścieżka*, *tryb*lub *strumień* jest wskaźnikiem typu null lub jeśli *Nazwa pliku* jest pustym ciągiem, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i zwracają **wartość null**.

Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Uwagi

Istnieją bardziej bezpieczne wersje tych funkcji, zobacz [freopen_s, _wfreopen_s](freopen-s-wfreopen-s.md).

Funkcja **freopen** zamyka plik aktualnie skojarzony ze *strumieniem* i ponownie przypisuje *strumień* do pliku określonego przez *ścieżkę*. **_wfreopen** to dwubajtowa wersja **_freopen**; argumenty *Path* i *mode* **_wfreopen** są ciągami znaków dwubajtowych. **_wfreopen** i **_freopen** zachowują się identycznie w inny sposób.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen**|**freopen**|**freopen**|**_wfreopen**|

**freopen** jest zwykle używany do przekierowywania wstępnie otwartych plików **stdin**, **stdout**i **stderr** do plików określonych przez użytkownika. Nowy plik skojarzony ze *strumieniem* jest otwarty z *trybem*, który jest ciągiem znaków określającym typ dostępu żądany dla pliku, w następujący sposób:

|*wyst*|Dostęp|
|-|-|
| **®** | Otwiera do odczytu. Jeśli plik nie istnieje lub nie można go znaleźć, wywołanie **freopen** kończy się niepowodzeniem. |
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
|**freopen**|\<stdio. h>|
|**_wfreopen**|\<stdio. h> lub \<WCHAR. h>|

Konsola nie jest obsługiwana w aplikacjach platforma uniwersalna systemu Windows (platformy UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane przed użyciem funkcji języka C w aplikacjach platformy UWP. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_freopen.c
// compile with: /W3
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.
#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   // Reassign "stderr" to "freopen.out":
   stream = freopen( "freopen.out", "w", stderr ); // C4996
   // Note: freopen is deprecated; consider using freopen_s instead

   if( stream == NULL )
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
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
