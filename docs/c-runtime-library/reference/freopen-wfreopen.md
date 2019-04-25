---
title: freopen, _wfreopen
ms.date: 11/04/2016
apiname:
- freopen
- _wfreopen
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
ms.openlocfilehash: 4c570837bddea1f5e986ae5f767279ab2637ea21
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332991"
---
# <a name="freopen-wfreopen"></a>freopen, _wfreopen

Ponownie przypisuje wskaźnik pliku. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [freopen_s —, _wfreopen_s —](freopen-s-wfreopen-s.md).

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

*Ścieżka*<br/>
Ścieżka nowego pliku.

*Tryb*<br/>
Dozwolony typ dostępu.

*stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do nowo otwartego pliku. Jeśli wystąpi błąd, oryginalny plik jest zamknięty, a funkcja zwraca **NULL** wartość wskaźnika. Jeśli *ścieżki*, *tryb*, lub *strumienia* jest wskaźnikiem typu null, lub jeśli *filename* jest pustym ciągiem, funkcje te wywołują nieprawidłowy parametr Program obsługi, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają **NULL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędu,.

## <a name="remarks"></a>Uwagi

Bardziej bezpieczne wersje tych funkcji istnieje, zobacz [freopen_s —, _wfreopen_s —](freopen-s-wfreopen-s.md).

**Freopen —** funkcji spowoduje zamknięcie pliku aktualnie skojarzone z *strumienia* i ponownie przypisuje *strumienia* do pliku określonego przez *ścieżki*. **_wfreopen —** to wersja znaku dwubajtowego **_freopen**; *ścieżki* i *tryb* argumenty **_wfreopen —** są ciągi znaków dwubajtowych. **_wfreopen —** i **_freopen** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen —**|**freopen —**|**freopen —**|**_wfreopen**|

**freopen —** jest zazwyczaj używana do przekierowania wstępnie otwarte pliki **stdin**, **stdout**, i **stderr** plików określone przez użytkownika. Nowy plik skojarzony z *strumienia* jest otwierany przy użyciu *tryb*, który jest ciągiem znaku, określający typ dostępu do żądanego pliku, w następujący sposób:

|*Tryb*|Access|
|-|-|
| **"r"** | Otwiera do odczytu. Jeśli plik nie istnieje lub nie można odnaleźć **freopen —** wywołanie zakończy się niepowodzeniem. |
| **"w"** | Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona. |
| **"a"** | Zostanie otwarty do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF), zanim nowe dane są zapisywane do pliku. Tworzy plik, jeśli nie istnieje. |
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
|**freopen —**|\<stdio.h>|
|**_wfreopen**|\<stdio.h > lub \<wchar.h >|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą, **stdin**, **stdout**, i **stderr**, muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
