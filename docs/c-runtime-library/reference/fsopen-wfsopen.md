---
title: _fsopen, _wfsopen
ms.date: 11/04/2016
api_name:
- _wfsopen
- _fsopen
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
helpviewer_keywords:
- opening files, streams
- fsopen function
- tfsopen function
- wfsopen function
- _fsopen function
- files [C++], opening
- _tfsopen function
- _wfsopen function
- file sharing [C++]
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
ms.openlocfilehash: 1ffc3aa5801ff2ed63ecf815f3351e4d7a8cf459
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956478"
---
# <a name="_fsopen-_wfsopen"></a>_fsopen, _wfsopen

Otwiera strumień z funkcją udostępniania plików.

## <a name="syntax"></a>Składnia

```C
FILE *_fsopen(
   const char *filename,
   const char *mode,
   int shflag
);
FILE *_wfsopen(
   const wchar_t *filename,
   const wchar_t *mode,
   int shflag
);
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Nazwa pliku do otwarcia.

*wyst*<br/>
Dozwolony typ dostępu.

*shflag*<br/>
Dozwolony typ udostępniania.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do strumienia. Wartość wskaźnika o wartości null wskazuje na błąd. Jeśli *Nazwa pliku* lub *tryb* ma **wartość null** lub jest pustym ciągiem, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **wartość null** i ustawiają **errno** na **EINVAL**.

Aby uzyskać więcej informacji o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_fsopen** otwiera plik określony przez *filename* jako strumień i przygotowuje plik do późniejszego udostępnionego odczytu lub zapisu zgodnie z definicją w argumentach Mode i *Shflag* . **_wfsopen** to dwubajtowa wersja **_fsopen**; argumenty *filename* i *mode* **_wfsopen** są ciągami znaków dwubajtowych. **_wfsopen** i **_fsopen** zachowują się identycznie w inny sposób.

*Tryb* ciągu znaków określa typ dostępu żądanego dla pliku, jak pokazano w poniższej tabeli.

|Termin|Definicja|
|----------|----------------|
|**®**|Otwiera do odczytu. Jeśli plik nie istnieje lub nie można go znaleźć, wywołanie **_fsopen** kończy się niepowodzeniem.|
|**k**|Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona.|
|**"a"**|Otwiera do zapisu na końcu pliku (dołączanie); najpierw tworzy plik, jeśli nie istnieje.|
|**"r +"**|Otwiera zarówno do odczytu, jak i do zapisu. (Plik musi istnieć).|
|**"w +"**|Otwiera pusty plik do odczytu i zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona.|
|**"a +"**|Otwiera do odczytu i dołączania; najpierw tworzy plik, jeśli nie istnieje.|

Używaj typów **"w"** i **"w +"** z ostrożnością, ponieważ mogą one zniszczyć istniejące pliki.

Gdy plik zostanie otwarty z typem dostępu **"a"** lub **"a +"** , wszystkie operacje zapisu są wykonywane na końcu pliku. Wskaźnik pliku można zmienić za pomocą [fseek](fseek-fseeki64.md) lub do [tyłu](rewind.md), ale zawsze jest on przenoszony z powrotem do końca pliku przed przeprowadzeniem operacji zapisu. W rezultacie istniejące dane nie mogą być zastępowane. W przypadku określenia typu dostępu **"r +"** , **"z +"** lub **"a +** " są dozwolone operacje odczytu i zapisu (plik jest otwierany do aktualizacji). Jednak podczas przełączania między operacjami odczytu i zapisu musi istnieć interwencja [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)lub do [tyłu](rewind.md) . W razie potrzeby można określić bieżącą pozycję dla operacji [fsetpos](fsetpos.md) lub [fseek](fseek-fseeki64.md) . Oprócz powyższych wartości jeden z następujących znaków może zostać uwzględniony w *trybie* do określenia trybu tłumaczenia dla nowych wierszy i zarządzania plikami.

|Termin|Definicja|
|----------|----------------|
|**t**|Otwiera plik w trybie tekst (przetłumaczony). W tym trybie kombinacje wysuwu wiersza (CR-LF) są tłumaczone na pojedyncze linie informacyjne (LF) na znaki wejściowe i LF są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W plikach otwartych do odczytu lub odczytu/zapisu, **_fsopen** sprawdza, czy Ctrl + Z na końcu pliku i usuwa go, jeśli to możliwe. Dzieje się tak, ponieważ użycie [fseek](fseek-fseeki64.md) i [ftell](ftell-ftelli64.md) do przenoszenia w pliku, który kończy się na Ctrl + z, może spowodować niewłaściwe zachowanie [fseek](fseek-fseeki64.md) na końcu pliku.|
|**b**|Otwiera plik w trybie binarnym (nieprzetłumaczonym); Powyższe tłumaczenia są pomijane.|
|**S**|Określa, że buforowanie jest zoptymalizowane dla, ale nie ograniczone do, dostęp sekwencyjny z dysku.|
|**R**|Określa, że buforowanie jest zoptymalizowane dla, ale nie ograniczone do, losowy dostęp z dysku.|
|**T**|Określa plik jako tymczasowy. Jeśli to możliwe, nie jest opróżniony na dysk.|
|**D**|Określa plik jako tymczasowy. Jest usuwany, gdy ostatni wskaźnik pliku jest zamknięty.|

Jeśli **t** lub **b** nie jest określony w *trybie*, tryb tłumaczenia jest definiowany przez zmienną trybu domyślnego **_fmode**. Jeśli **t** lub **b** jest poprzedzony argumentem, funkcja kończy się niepowodzeniem i zwraca **wartość null**. Aby zapoznać się z omówieniem trybów tekstowych i binarnych, zobacz [plik tekstowy i tryb binarny we/wy](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Argument *Shflag* jest wyrażeniem stałym składającym się z jednej z następujących stałych manifestu, zdefiniowanych w udziale. h.

|Termin|Definicja|
|----------|----------------|
|**_SH_COMPAT**|Ustawia tryb zgodności dla aplikacji 16-bitowych.|
|**_SH_DENYNO**|Zezwala na dostęp do odczytu i zapisu.|
|**_SH_DENYRD**|Nie zezwala na dostęp do odczytu do pliku.|
|**_SH_DENYRW**|Nie zezwala na dostęp do odczytu i zapisu do pliku.|
|**_SH_DENYWR**|Odmawia dostępu do zapisu w pliku.|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Dla stałej manifestu dla parametru *Shflag* .|
|**_wfsopen**|\<stdio. h > lub \<WCHAR. h >|\<share.h><br /><br /> Dla stałej manifestu dla parametru *Shflag* .|

## <a name="example"></a>Przykład

```C
// crt_fsopen.c

#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   FILE *stream;

   // Open output file for writing. Using _fsopen allows us to
   // ensure that no one else writes to the file while we are
   // writing to it.
    //
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )
   {
      fprintf( stream, "No one else in the network can write "
                       "to this file until we are done.\n" );
      fclose( stream );
   }
   // Now others can write to the file while we read it.
   system( "type outfile" );
}
```

```Output
No one else in the network can write to this file until we are done.
```

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
