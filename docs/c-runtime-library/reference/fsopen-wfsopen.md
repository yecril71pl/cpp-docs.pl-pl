---
title: _fsopen, _wfsopen
ms.date: 11/04/2016
apiname:
- _wfsopen
- _fsopen
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
ms.openlocfilehash: 197a4f690a6626edbfec27ea4abef1999b6cedaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677490"
---
# <a name="fsopen-wfsopen"></a>_fsopen, _wfsopen

Zostanie otwarty strumień, z funkcją Udostępnianie plików.

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
Nazwa pliku, aby otworzyć.

*Tryb*<br/>
Dozwolony typ dostępu.

*shflag*<br/>
Typ udostępniania dozwolone.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do strumienia. Wartość null wskaźnika wskazuje na błąd. Jeśli *filename* lub *tryb* jest **NULL** lub pustym ciągiem, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Walidacja parametru ](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **NULL** i ustaw **errno** do **EINVAL**.

Aby uzyskać więcej informacji na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Fsopen —** funkcji spowoduje otwarcie pliku określonego przez *filename* jako strumienia i przygotowuje go do kolejnych udostępnionego odczytu lub zapisu, zgodnie z definicją w trybie i *shflag*argumentów. **_wfsopen —** to wersja znaku dwubajtowego **_fsopen —**; *filename* i *tryb* argumenty **_wfsopen —** są ciągi znaków dwubajtowych. **_wfsopen —** i **_fsopen —** zachowują się identycznie.

Ciąg znaków *tryb* określa rodzaj dostępu do żądanego pliku, jak pokazano w poniższej tabeli.

|Termin|Definicja|
|----------|----------------|
|**"r"**|Otwiera do odczytu. Jeśli plik nie istnieje lub nie można odnaleźć **_fsopen —** wywołanie zakończy się niepowodzeniem.|
|**"w"**|Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona.|
|**""**|Zostanie otwarty do zapisu na końcu pliku (dołączanie); najpierw tworzy plik, jeśli nie istnieje.|
|**"r +"**|Otwiera Odczyt i zapis. (Plik musi istnieć).|
|**"w +"**|Otwiera pusty plik Odczyt i zapis. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona.|
|**"+"**|Otwiera do odczytu i dołączania; najpierw tworzy plik, jeśli nie istnieje.|

Użyj **"w"** i **"w +"** typów z rozwagą, zgodnie z ich może zniszczyć istniejących plików.

Po otwarciu pliku za pomocą **""** lub **"+"** uzyskiwać dostępu do typu, wszystkie operacje zapisu występują na końcu pliku. Wskaźnik pliku może być przeniesiony za pomocą [fseek](fseek-fseeki64.md) lub [rewind](rewind.md), ale on jest zawsze przenoszony z powrotem na koniec pliku przed wszelkie zapisu operacji jest przeprowadzane. W związku z tym nie można zastąpić istniejące dane. Gdy **"r +"**, **"w +"**, lub **"+"** jest określony typ dostępu, Odczyt i zapis są dozwolone (plik jest nazywany otwarte na potrzeby aktualizacji). Jednak podczas przełączania między Odczyt i zapis, musi istnieć interwencyjne [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md), lub [rewind](rewind.md) operacji. Bieżąca pozycja może być określona dla [fsetpos](fsetpos.md) lub [fseek](fseek-fseeki64.md) operacji, w razie potrzeby. Oprócz powyższych wartości jednego z następujących znaków mogą być dołączane *tryb* określić tryb translacji dla nowych wierszy i zarządzanie plikami.

|Termin|Definicja|
|----------|----------------|
|**t**|Otwiera plik w trybie tekstowym (tłumaczonym). W tym trybie wiersza powrotu karetki kanału informacyjnego kombinacji (CR-LF) są tłumaczone na jeden wiersz źródła danych (LF) na dane wejściowe i znaki wysuwu wiersza są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W przypadku plików otwartych do odczytu lub odczytu/zapisu **_fsopen —** wyszukuje klawisze CTRL + Z końcem pliku i usuwa go, jeśli jest to możliwe. Odbywa się, ponieważ używa [fseek](fseek-fseeki64.md) i [ftell —](ftell-ftelli64.md) można przenieść w pliku, który kończy się znakiem CRTL + Z, może spowodować [fseek](fseek-fseeki64.md) działać nieprawidłowo w pobliżu końca pliku.|
|**b**|Otwiera plik w trybie binarnym (nieprzetłumaczonym); Powyższe tłumaczenia są pomijane.|
|**S**|Określa, że buforowanie jest zoptymalizowane pod kątem, ale nie ogranicza się do dostępu sekwencyjnego do dysku.|
|**R**|Określa, że buforowanie jest zoptymalizowane pod kątem, ale nie ogranicza się do dostępu losowego do dysku.|
|**T**|Określa plik jako tymczasowy. Jeśli to możliwe, nie jest on opróżniany do dysku.|
|**D**|Określa plik jako tymczasowy. Jest usuwany po zamknięciu ostatniego wskaźnika do pliku.|

Jeśli **t** lub **b** nie jest podana w *tryb*, tryb translacji jest zdefiniowany przez zmienną trybu domyślnego **_fmode**. Jeśli **t** lub **b** jest umieszczany przez argument, funkcja kończy się niepowodzeniem i zwraca **NULL**. Aby uzyskać informacje o trybach tekstowym i binarnym, zobacz [tekstowych i binarnych We/Wy trybu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Argument *shflag* jest wyrażeniem stałym, składający się z jednego z następujących stałych manifestu, określonych w Share.h.

|Termin|Definicja|
|----------|----------------|
|**_SH_COMPAT**|Ustawia tryb zgodności dla 16-bitowych aplikacji.|
|**_SH_DENYNO**|Zezwala uprawnienia odczytu i zapisu.|
|**_SH_DENYRD**|Nie zezwala na dostęp do odczytu do pliku.|
|**_SH_DENYRW**|Nie zezwala na odczyt i zapis do pliku.|
|**_SH_DENYWR**|Nie zezwala na dostęp do zapisu do pliku.|

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen —**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Dla stałych manifestu dla *shflag* parametru.|
|**_wfsopen**|\<stdio.h > lub \<wchar.h >|\<share.h><br /><br /> Dla stałych manifestu dla *shflag* parametru.|

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

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
