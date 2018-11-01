---
title: _dupenv_s_dbg, _wdupenv_s_dbg
ms.date: 11/04/2016
apiname:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
apitype: DLLExport
f1_keywords:
- _tdupenv_s_dbg
- _dupenv_s_dbg
- _wdupenv_s_dbg
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
ms.openlocfilehash: 95d8c18a0ebc543304fdb6bf51c4adde589333aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579603"
---
# <a name="dupenvsdbg-wdupenvsdbg"></a>_dupenv_s_dbg, _wdupenv_s_dbg

Pobieranie wartości z bieżącego środowiska.  Wersje [_dupenv_s —, _wdupenv_s —](dupenv-s-wdupenv-s.md) , przydziel pamięć z [_malloc_dbg](malloc-dbg.md) podać dodatkowe informacje debugowania.

## <a name="syntax"></a>Składnia

```C
errno_t _dupenv_s_dbg(
   char **buffer,
   size_t *numberOfElements,
   const char *varname,
   int blockType,
   const char *filename,
   int linenumber
);
errno_t _wdupenv_s_dbg(
   wchar_t **buffer,
   size_t * numberOfElements,
   const wchar_t *varname,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Bufor do przechowywania wartości zmiennej.

*numberOfElements*<br/>
Rozmiar *buforu*.

*Nazwa zmiennej*<br/>
Nazwa zmiennej środowiskowej.

*blockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

Zero, w przypadku powodzenia, kod błędu.

Te funkcje sprawdzają poprawność parametrów; Jeśli *buforu* lub *nazwa_zmiennej* jest **NULL**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje ustawiają **errno** do **EINVAL** i zwracają **EINVAL**.

Jeśli te funkcje nie może przydzielić wystarczającej ilości pamięci, ustawiają *buforu* do **NULL** i *numberOfElements* do 0 i zwracają **ENOMEM**.

## <a name="remarks"></a>Uwagi

**_Dupenv_s_dbg —** i **_wdupenv_s_dbg —** funkcje są takie same jak **_dupenv_s —** i **_wdupenv_s —** z tą różnicą, że gdy **_DEBUG** jest zdefiniowany, te funkcje używają wersji debugowania [— funkcja malloc](malloc.md), [_malloc_dbg](malloc-dbg.md), można przydzielić pamięci dla wartości zmiennej środowiskowej. Instrukcje dotyczące debugowania funkcji **_malloc_dbg**, zobacz [_malloc_dbg](malloc-dbg.md).

Nie trzeba jawnie wywołać w większości przypadków te funkcje. Zamiast tego można określić flagę **_CRTDBG_MAP_ALLOC**. Gdy **_CRTDBG_MAP_ALLOC** jest zdefiniowany, wywołania **_dupenv_s —** i **_wdupenv_s —** są mapowane ponownie do **_dupenv_s_dbg —** i **_wdupenv_s_dbg —**, odpowiednio, z *blockType* równa **_NORMAL_BLOCK**. Dzięki temu, nie trzeba jawnie wywołać te funkcje, chyba że chcesz oznaczyć bloki stosu jako **_CLIENT_BLOCK**. Aby uzyskać więcej informacji na temat typów bloków, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s_dbg —**|**_dupenv_s_dbg**|**_dupenv_s_dbg**|**_wdupenv_s_dbg**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_dupenv_s_dbg**|\<crtdbg.h>|
|**_wdupenv_s_dbg**|\<crtdbg.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_dupenv_s_dbg.c
#include  <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Stałe środowiska](../../c-runtime-library/environmental-constants.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
