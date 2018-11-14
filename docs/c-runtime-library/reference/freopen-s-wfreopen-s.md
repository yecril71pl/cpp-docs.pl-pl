---
title: freopen_s, _wfreopen_s
ms.date: 11/04/2016
apiname:
- _wfreopen_s
- freopen_s
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
ms.openlocfilehash: 2cdc16f21882c32933868000c6fd1d66accc74b8
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326515"
---
# <a name="freopens-wfreopens"></a>freopen_s, _wfreopen_s

Ponownie przypisuje wskaźnik pliku. Te wersje [freopen —, _wfreopen —](freopen-wfreopen.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Wskaźnik do wskaźnika pliku muszą być dostarczone przez wywołanie.

*Ścieżka*<br/>
Ścieżka nowego pliku.

*Tryb*<br/>
Dozwolony typ dostępu.

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca kod błędu. Jeśli wystąpi błąd, oryginalnym pliku jest zamknięty.

## <a name="remarks"></a>Uwagi

**Freopen_s —** funkcji spowoduje zamknięcie pliku aktualnie skojarzone z *strumienia* i ponownie przypisuje *strumienia* do pliku określonego przez *ścieżki* . **_wfreopen_s —** to wersja znaku dwubajtowego **_freopen_s**; *ścieżki* i *tryb* argumenty **_wfreopen_s —** są ciągi znaków dwubajtowych. **_wfreopen_s —** i **_freopen_s** zachowują się identycznie.

Jeśli dowolny z *pFile*, *ścieżki*, *tryb*, lub *strumienia* są **o wartości NULL**, lub jeśli *ścieżki* jest pustym ciągiem, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s —**|**freopen_s —**|**freopen_s —**|**_wfreopen_s**|

**freopen_s —** jest zazwyczaj używana do przekierowania wstępnie otwarte pliki **stdin**, **stdout**, i **stderr** plików określone przez użytkownika. Nowy plik skojarzony z *strumienia* jest otwierany przy użyciu *tryb*, który jest ciągiem znaku, określający typ dostępu do żądanego pliku, w następujący sposób:

|*Tryb*|Access|
|-|-|
| **"r"** | Otwiera do odczytu. Jeśli plik nie istnieje lub nie można odnaleźć **freopen_s —** wywołanie zakończy się niepowodzeniem. |
| **"w"** | Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona. |
| **""** | Zostanie otwarty do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF), zanim nowe dane są zapisywane do pliku. Tworzy plik, jeśli nie istnieje. |
| **"r +"** | Otwiera Odczyt i zapis. Plik musi istnieć. |
| **"w +"** | Otwiera pusty plik Odczyt i zapis. Jeśli plik istnieje, jego zawartość zostaje zniszczona. |
| **"+"** | Otwiera do odczytu i dołączania. Operacja dołączania obejmuje usunięcie znacznika EOF, zanim nowe dane są zapisywane do pliku. Znacznik EOF nie jest przywracany po zakończeniu zapisu. Tworzy plik, jeśli nie istnieje. |

Użyj **"w"** i **"w +"** typów z rozwagą, zgodnie z ich może zniszczyć istniejących plików.

Po otwarciu pliku za pomocą **""** lub **"+"** dostęp typu zapis wszystkich operacji miejsce na końcu pliku. Mimo że wskaźnik pliku może być przeniesiony za pomocą [fseek](fseek-fseeki64.md) lub [rewind](rewind.md), wskaźnik pliku jest zawsze przenoszony z powrotem na koniec pliku przed wszelkie zapisu operacji jest przeprowadzane. W związku z tym nie można zastąpić istniejące dane.

**""** Trybu nie usuwa znacznika EOF przed dołączeniem do pliku. Po wystąpieniu operacji dołączania, polecenie MS-DOS TYPE pokazuje tylko dane przed oryginalnym znacznikiem EOF i nie żadnych danych dołączonych do pliku. **"+"** Tryb usuwa znacznika EOF przed dołączeniem do pliku. Po operacji dołączania polecenie MS-DOS TYPE pokazuje wszystkie dane w pliku. **"+"** Tryb jest wymagany do wykonania operacji dołączania do pliku strumienia, który jest kończony przy użyciu CTRL + Z określającego znacznik EOF.

Gdy **"r +"**, **"w +"**, lub **"+"** jest określony typ dostępu, Odczyt i zapis są dozwolone (plik jest określany jako otwarty do "aktualizacji"). Jednak podczas przełączania się między Odczyt i zapis, musi istnieć interwencyjne [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), lub [rewind](rewind.md) operacji. Bieżąca pozycja może być określona dla [fsetpos](fsetpos.md) lub [fseek](fseek-fseeki64.md) operacji, w razie potrzeby. Oprócz powyższych wartości jednego z następujących znaków mogą zostać zawarte w *tryb* ciągu, aby określić tryb translacji dla nowych wierszy.

|*tryb* modyfikator|Tryb translacji|
|-|-|
| **t** | Otwórz w tekście (tłumaczonym) trybu. |
| **b** | Otwórz w trybie binarnym (nieprzetłumaczonym); tłumaczenia znaków powrotu karetki i wysuwu wiersza są pomijane. |

W trybie tekstowym (tłumaczonym) kombinacje powrotu wysuwu wiersza (CR-LF) powrotu karetki są tłumaczone na znaki pojedynczego wysuwu wiersza (LF) na dane wejściowe Znaki wysuwu wiersza są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W plikach otworzyć do odczytu lub zapisu i odczytu z **"+"**, biblioteki wykonawczej wyszukuje klawisze CTRL + Z końcem pliku i usuwa go, jeśli jest to możliwe. Odbywa się, ponieważ używa [fseek](fseek-fseeki64.md) i [ftell —](ftell-ftelli64.md) można przenieść w pliku może spowodować, że [fseek](fseek-fseeki64.md) działać nieprawidłowo w pobliżu końca pliku. **t** opcji jest rozszerzeniem firmy Microsoft, które nie mają być używane gdzie pożądana jest przenośność kodowania ANSI.

Jeśli **t** lub **b** nie jest podana w *tryb*, domyślny tryb translacji jest zdefiniowany przez zmienną globalną [_fmode](../../c-runtime-library/fmode.md). Jeśli **t** lub **b** jest umieszczany przez argument, funkcja kończy się niepowodzeniem i zwraca **NULL**.

Aby uzyskać informacje o trybach tekstowym i binarnym, zobacz [tekstowych i binarnych We/Wy trybu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**freopen_s —**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h > lub \<wchar.h >|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą, **stdin**, **stdout**, i **stderr**, muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
