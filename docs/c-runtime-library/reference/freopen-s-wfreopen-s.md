---
title: freopen_s —, _wfreopen_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04b136a46672838fd6ee554668353d92796abc7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405552"
---
# <a name="freopens-wfreopens"></a>freopen_s, _wfreopen_s

Ponownie przypisuje wskaźnika pliku. Te wersje programu [freopen —, _wfreopen —](freopen-wfreopen.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Wskaźnik do wskaźnika pliku dostarczanych przez wywołanie.

*Ścieżka*<br/>
Ścieżka do nowego pliku.

*Tryb*<br/>
Dozwolonego typu dostępu.

*Strumień*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca kod błędu. Jeśli wystąpi błąd, oryginalny plik jest zamknięty.

## <a name="remarks"></a>Uwagi

**Freopen_s —** funkcji spowoduje zamknięcie pliku, w obecnie skojarzony z *strumienia* i następuje zmiana przypisania *strumienia* do pliku określonego przez *ścieżki* . **_wfreopen_s —** jest wersja znaków dwubajtowych **_freopen_s**; *ścieżki* i *tryb* argumenty **_wfreopen_s —** są ciągi znaków dwubajtowych. **_wfreopen_s —** i **_freopen_s** zachowują się tak samo w przeciwnym razie wartość.

Jeśli dowolny z *pFile*, *ścieżki*, *tryb*, lub *strumienia* są **NULL**, lub jeśli *ścieżka* jest pustym ciągiem, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwracać **einval —**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s —**|**freopen_s —**|**freopen_s —**|**_wfreopen_s**|

**freopen_s —** jest zwykle używana do przekierowywania wstępnie otwarte pliki **stdin**, **stdout**, i **stderr** do plików określone przez użytkownika. Nowy plik skojarzony z *strumienia* jest otwierany z *tryb*, która jest ciąg znaków określający typ dostępu do żądanego pliku, w następujący sposób:

|*Tryb*|Access|
|-|-|
**"r"**|Zostanie otwarty do odczytu. Jeśli plik nie istnieje lub nie można znaleźć, **freopen_s —** wywołać kończy się niepowodzeniem.
**"w"**|Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.
**""**|Zostanie otwarty do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF), zanim nowe dane zostają zapisane do pliku. Tworzy plik, jeśli nie istnieje.
**"r +"**|Otwiera odczytywanie i zapisywanie. Plik musi istnieć.
**"w +"**|Otwiera pusty plik na odczytywanie i zapisywanie. Jeśli plik istnieje, jego zawartość zostaną zniszczone.
**"+"**|Zostanie otwarty do odczytu i dołączenie kodu. Dołączanie operacja obejmuje usunięcie znacznik EOF przed nowe dane zostają zapisane do pliku. Znacznik EOF nie jest przywracany po zakończeniu zapisu. Tworzy plik, jeśli nie istnieje.

Użyj **"w"** i **"w +"** typy z ostrożnością, zgodnie z ich zniszczyć istniejące pliki.

Gdy plik jest otwarty z **""** lub **"+"** dostęp typu zapis wszystkich operacji miejsce na końcu pliku. Mimo że może być położenia wskaźnika pliku przy użyciu [fseek](fseek-fseeki64.md) lub [rewind](rewind.md), wskaźnika pliku jest zawsze przeniesiony z powrotem na koniec pliku przed żadnego zapisu, wykonywane są wymienione. W związku z tym nie można zastąpić istniejące dane.

**""** Trybu nie powoduje usunięcia znacznik EOF przed dołączeniem do pliku. Po wystąpił dołączanie polecenia typu MS-DOS przedstawia tylko dane do oryginalnego znacznik EOF i nie dołączane do pliku. **"+"** Tryb, usuń znacznik EOF przed dołączeniem do pliku. Po dołączeniu, polecenie typu MS-DOS Wyświetla wszystkie dane w pliku. **"+"** Tryb jest wymagany do dołączenia do pliku strumienia, który kończy się znakiem znacznik EOF CTRL + Z.

Gdy **"r +"**, **"w +"**, lub **"+"** określono typ dostępu, odczytywanie i zapisywanie są dozwolone (plik jest określany jako otwarte dla "update"). Jednak podczas przełączania się między odczytu i zapisu, musi być aktywne [fsetpos —](fsetpos.md), [fseek](fseek-fseeki64.md), lub [rewind](rewind.md) operacji. Bieżąca pozycja można określić dla [fsetpos —](fsetpos.md) lub [fseek](fseek-fseeki64.md) operacji, w razie potrzeby. Oprócz powyższych wartości jednego z następujących znaków może być zawarta w *tryb* ciąg, aby określić tryb tłumaczenia dla nowych wierszy.

|*tryb* modyfikator|Tryb tłumaczenia|
|-|-|
**t**|Otwórz w tekście (translacji) trybu.
**b**|Otwórz w trybie binarnym (niezrozumiały); Tłumaczenie obejmujące znaki powrotu karetki i wysuwu wiersza są pomijane.

W trybie tekstowym (translacji) kombinacje powrotu wysuwu wiersza (CR LF) karetki są tłumaczone na znaki wysuwu wiersza pojedynczego (LF) w danych wejściowych; LF znaki są tłumaczone na kombinacje CR LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako plik końcowy znak wejściowy. W plikach otwarty do odczytu lub zapisu i odczytu z **"+"**, biblioteki wykonawczej wyszukuje klawisze CTRL + Z końcem pliku i usuwa go, jeśli to możliwe. Jest to zrobić, ponieważ używa [fseek](fseek-fseeki64.md) i [ftell —](ftell-ftelli64.md) można przenieść w pliku może spowodować [fseek](fseek-fseeki64.md) będzie działać nieprawidłowo zbliża się koniec pliku. **t** opcja to rozszerzenie firmy Microsoft, które nie powinny być używane których przenośność ANSI jest potrzebne.

Jeśli **t** lub **b** nie została podana w *tryb*, domyślny tryb tłumaczenia jest definiowana za pomocą zmiennej globalnej [_fmode —](../../c-runtime-library/fmode.md). Jeśli **t** lub **b** jest prefiksem argument, funkcja kończy się niepowodzeniem i zwraca **NULL**.

Omówienie trybach tekstowym i binarnym, zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**freopen_s —**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h > lub \<wchar.h >|

Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu **stdin**, **stdout**, i **stderr**, muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
