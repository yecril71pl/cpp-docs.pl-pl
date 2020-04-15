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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a24e34ead905d2f704bfbf4d829064c656272e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345918"
---
# <a name="freopen_s-_wfreopen_s"></a>freopen_s, _wfreopen_s

Ponowne przypisywanie wskaźnika pliku. Te wersje [freopen, _wfreopen](freopen-wfreopen.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*p Plik*<br/>
Wskaźnik do wskaźnika pliku, który ma być dostarczony przez wywołanie.

*Ścieżka*<br/>
Ścieżka nowego pliku.

*Tryb*<br/>
Dozwolony typ dostępu.

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca kod błędu. Jeśli wystąpi błąd, oryginalny plik zostanie zamknięty.

## <a name="remarks"></a>Uwagi

Funkcja **freopen_s** zamyka plik aktualnie skojarzony ze *strumieniem* i ponownie przywdymuje *strumień* do pliku określonego przez *ścieżkę*. **_wfreopen_s** jest szerokoznakową wersją **_freopen_s**; argumenty *ścieżki* i *trybu* do **_wfreopen_s** są ciągami znaków o szerokich znakach. **_wfreopen_s** i **_freopen_s** zachowują się identycznie w przeciwnym razie.

Jeśli którykolwiek z *pFile*, *path*, *mode*lub *stream* mają **wartość NULL**lub jeśli *ścieżka* jest pustym ciągiem, te funkcje wywołują nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje **ustawiają errno** na **EINVAL** i zwracają **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s** jest zazwyczaj używany do przekierowania wstępnie otwartych plików **stdin**, **stdout**i **stderr** do plików określonych przez użytkownika. Nowy plik skojarzony ze *strumieniem* jest otwierany w *trybie*, który jest ciągiem znaków określającym typ dostępu żądanego dla pliku, w następujący sposób:

|*Tryb*|Dostęp|
|-|-|
| **"r"** | Otwiera się do czytania. Jeśli plik nie istnieje lub nie można go odnaleźć, **wywołanie freopen_s** nie powiedzie się. |
| **"w"** | Otwiera pusty plik do zapisania. Jeśli dany plik istnieje, jego zawartość zostanie zniszczona. |
| **"a"** | Otwiera się do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF) przed zapisaniem nowych danych w pliku. Tworzy plik, jeśli nie istnieje. |
| **"r+"** | Otwiera się zarówno do czytania, jak i pisania. Plik musi istnieć. |
| **"w+"** | Otwiera pusty plik do odczytu i zapisu. Jeśli plik istnieje, jego zawartość zostanie zniszczona. |
| **"a+"** | Otwiera do czytania i dołączania. Operacja dołączania obejmuje usunięcie znacznika EOF przed zapisaniem nowych danych w pliku. Znacznik EOF nie zostanie przywrócony po zakończeniu zapisu. Tworzy plik, jeśli nie istnieje. |

Użyj typów **"w"** i **"w+"** ostrożnie, ponieważ mogą one zniszczyć istniejące pliki.

Po otwarciu pliku z typem dostępu **"a"** lub **"a+",** wszystkie operacje zapisu odbywają się na końcu pliku. Mimo że wskaźnik pliku można zmienić za pomocą [fseek](fseek-fseeki64.md) lub [przewinąć](rewind.md)do tyłu, wskaźnik pliku jest zawsze przenoszony z powrotem na koniec pliku przed przeprowadzeniem jakiejkolwiek operacji zapisu. W związku z tym istniejące dane nie mogą być zastąpione.

Tryb **"a"** nie usuwa znacznika EOF przed dołączeniem do pliku. Po dołączeniu polecenie MS-DOS TYPE pokazuje tylko dane do oryginalnego znacznika EOF, a nie wszystkie dane dołączone do pliku. Tryb **"a+"** usuwa znacznik EOF przed dołączeniem do pliku. Po dołączeniu polecenie MS-DOS TYPE pokazuje wszystkie dane w pliku. Tryb **"a+"** jest wymagany do dołączania do pliku strumienia, który jest zakończony znacznikiem CTRL+Z EOF.

Po określeniu typu dostępu **"r+",** **"w+"** lub **"a+"** dozwolone jest zarówno odczyt, jak i zapis (mówi się, że plik jest otwarty dla "aktualizacji"). Jednak podczas przełączania między odczytem a zapisem musi być interweniująca [operacja fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)lub [do tyłu.](rewind.md) W razie potrzeby można określić bieżącą pozycję dla operacji [fsetpos](fsetpos.md) lub [fseek.](fseek-fseeki64.md) Oprócz powyższych wartości, jeden z następujących znaków może być uwzględniony w ciągu *trybu,* aby określić tryb tłumaczenia dla nowych wierszy.

|modyfikator *trybu*|Tryb tłumaczenia|
|-|-|
| **t** | Otwórz w trybie tekstowym (przetłumaczonym). |
| **B** | Otwarte w trybie binarnym (nieprzetłumaczonym); tłumaczenia obejmujące znaki powrotu karetki i wiersza są pomijane. |

W trybie tekstowym (przetłumaczonym) kombinacje kanału informacyjnego wiersza powrotu karetki (CR-LF) są tłumaczone na znaki jednowierszowego kanału informacyjnego (LF) na wejściu; Znaki LF są tłumaczone na kombinacje CR-LF na wyjściu. Ponadto CTRL+Z jest interpretowany jako znak końca pliku na danych wejściowych. W plikach otwartych do odczytu lub do zapisu i odczytu za pomocą **"a+"** biblioteka czasu wykonywania sprawdza, czy ctrl+ Z na końcu pliku i usuwa go, jeśli to możliwe. Dzieje się tak, ponieważ za pomocą [fseek](fseek-fseeki64.md) i [ftell](ftell-ftelli64.md) przenieść w pliku może spowodować [fseek](fseek-fseeki64.md) zachowywać się nieprawidłowo pod koniec pliku. T **t** Opcja jest rozszerzeniem firmy Microsoft, które nie powinno być używane tam, gdzie wymagana jest przenośność ANSI.

Jeśli **t** lub **b** nie jest podany w *trybie,* domyślny tryb tłumaczenia jest zdefiniowany przez zmienną globalną [_fmode](../../c-runtime-library/fmode.md). Jeśli **argument jest** poprzedzony t lub **b,** funkcja kończy się niepowodzeniem i zwraca **wartość NULL**.

Aby zapoznać się z omówieniami trybów tekstowych i binarnych, zobacz [We/Wy pliku w trybie tekstowym i binarnym](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> lub \<wchar.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej systemu Windows (UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane, zanim funkcje c w czasie wykonywania mogą z nich korzystać w aplikacjach platformy uniwersalnej systemu Windows. Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
