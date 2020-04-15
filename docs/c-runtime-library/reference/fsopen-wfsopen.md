---
title: _fsopen, _wfsopen
ms.date: 4/2/2020
api_name:
- _wfsopen
- _fsopen
- _o__fsopen
- _o__wfsopen
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
ms.openlocfilehash: 49907808729375e3bea18a5f4bbf204852e0072a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345699"
---
# <a name="_fsopen-_wfsopen"></a>_fsopen, _wfsopen

Otwiera strumień z udostępnianiem plików.

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

*Pod nazwą*<br/>
Nazwa pliku do otwarcia.

*Tryb*<br/>
Dozwolony typ dostępu.

*żużel*<br/>
Dozwolony typ udostępniania.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do strumienia. Wartość wskaźnika zerowego wskazuje błąd. Jeśli *nazwa pliku* lub *tryb* ma wartość **NULL** lub pusty ciąg, funkcje te wywołują nieprawidłowy program obsługi parametrów, zgodnie z opisem w polu Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje zwracają **wartość NULL** i **ustawiają errno** na **EINVAL**.

Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_fsopen** otwiera plik określony przez *nazwę pliku* jako strumień i przygotowuje plik do późniejszego wspólnego odczytu lub zapisu, zgodnie z definicją w trybie i argumentach *żużla.* **_wfsopen** jest szerokoznakową wersją **_fsopen**; argumenty *nazwy pliku* i *trybu* do **_wfsopen** są ciągami znaków o szerokich znakach. **_wfsopen** i **_fsopen** zachowują się identycznie w przeciwnym razie.

*Tryb* ciągu znaków określa typ dostępu żądanego dla pliku, jak pokazano w poniższej tabeli.

|Termin|Definicja|
|----------|----------------|
|**"r"**|Otwiera się do czytania. Jeśli plik nie istnieje lub nie można go odnaleźć, **wywołanie _fsopen** nie powiedzie się.|
|**"w"**|Otwiera pusty plik do zapisania. Jeśli dany plik istnieje, jego zawartość zostanie zniszczona.|
|**"a"**|Otwiera do zapisu na końcu pliku (dołączanie); najpierw tworzy plik, jeśli nie istnieje.|
|**"r+"**|Otwiera się zarówno do czytania, jak i pisania. (Plik musi istnieć).|
|**"w+"**|Otwiera pusty plik do odczytu i zapisu. Jeśli dany plik istnieje, jego zawartość zostanie zniszczona.|
|**"a+"**|Otwiera do czytania i dołączania; najpierw tworzy plik, jeśli nie istnieje.|

Użyj typów **"w"** i **"w+"** ostrożnie, ponieważ mogą one zniszczyć istniejące pliki.

Po otwarciu pliku z typem dostępu **"a"** lub **"a+",** wszystkie operacje zapisu występują na końcu pliku. Wskaźnik pliku można zmienić położenie za pomocą [fseek](fseek-fseeki64.md) lub [przewinąć](rewind.md)do tyłu , ale jest zawsze przenoszony z powrotem na koniec pliku przed przeprowadzeniem jakiejkolwiek operacji zapisu. W związku z tym istniejące dane nie mogą być zastąpione. Po określeniu typu dostępu **"r+",** **"w+"** lub **"a+"** dozwolone jest zarówno odczyt, jak i zapis (mówi się, że plik jest otwarty do aktualizacji). Jednak podczas przełączania między odczytem a zapisem musi być interweniująca [operacja fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)lub [do tyłu.](rewind.md) W razie potrzeby można określić bieżącą pozycję dla operacji [fsetpos](fsetpos.md) lub [fseek.](fseek-fseeki64.md) Oprócz powyższych wartości, jeden z następujących znaków może być uwzględniony w *trybie,* aby określić tryb tłumaczenia dla nowych wierszy i do zarządzania plikami.

|Termin|Definicja|
|----------|----------------|
|**t**|Otwiera plik w trybie tekstowym (przetłumaczonym). W tym trybie kombinacje kanału informacyjnego wiersza powrotu karetki (CR-LF) są tłumaczone na pojedyncze kanały informacyjne (LF) na wejściu, a znaki LF są tłumaczone na kombinacje CR-LF na wyjściu. Ponadto CTRL+Z jest interpretowany jako znak końca pliku na danych wejściowych. W plikach otwartych do odczytu lub odczytu/zapisu **_fsopen** sprawdza, czy na końcu pliku znajduje się ctrl+Z i usuwa go, jeśli to możliwe. Dzieje się tak, ponieważ za pomocą [fseek](fseek-fseeki64.md) i [ftell](ftell-ftelli64.md) przenieść w pliku, który kończy się CTRL + Z może spowodować [fseek](fseek-fseeki64.md) zachowywać się nieprawidłowo na końcu pliku.|
|**B**|Otwiera plik w trybie binarnym (nieprzetłumaczonym); powyższe tłumaczenia są pomijane.|
|**S**|Określa, że buforowanie jest zoptymalizowane pod kątem sekwencyjnego dostępu z dysku, ale nie ogranicza się do niego.|
|**R**|Określa, że buforowanie jest zoptymalizowane pod kątem losowego dostępu z dysku, ale nie ogranicza się do niego.|
|**T**|Określa plik jako tymczasowy. Jeśli to możliwe, nie jest opróżniany na dysk.|
|**D**|Określa plik jako tymczasowy. Jest on usuwany po zamknięciu ostatniego wskaźnika pliku.|

Jeśli **t** lub **b** nie jest podany w *trybie,* tryb tłumaczenia jest zdefiniowany przez zmienną trybu domyślnego **_fmode**. Jeśli **argument jest** poprzedzony t lub **b,** funkcja kończy się niepowodzeniem i zwraca **wartość NULL**. Aby zapoznać się z omówieniami trybów tekstowych i binarnych, zobacz [We/Wy pliku w trybie tekstowym i binarnym](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Argument *shflag* jest wyrażeniem stałym składającym się z jednej z następujących stałych manifestu, zdefiniowanej w Share.h.

|Termin|Definicja|
|----------|----------------|
|**_SH_COMPAT**|Ustawia tryb zgodności dla aplikacji 16-bitowych.|
|**_SH_DENYNO**|Zezwala na dostęp do odczytu i zapisu.|
|**_SH_DENYRD**|Odmawia dostępu do odczytu do pliku.|
|**_SH_DENYRW**|Odmawia dostępu do odczytu i zapisu do pliku.|
|**_SH_DENYWR**|Odmawia dostępu do zapisu do pliku.|

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<> akcji.h<br /><br /> Dla stałej manifestu dla *parametru shflag.*|
|**_wfsopen**|\<stdio.h> lub \<wchar.h>|\<> akcji.h<br /><br /> Dla stałej manifestu dla *parametru shflag.*|

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

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
