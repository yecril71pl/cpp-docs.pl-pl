---
title: _dupenv_s_dbg, _wdupenv_s_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ef129cec096734c23e911a5dc77bf3bd0b2df03
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404308"
---
# <a name="dupenvsdbg-wdupenvsdbg"></a>_dupenv_s_dbg, _wdupenv_s_dbg

Pobieranie wartości z bieżącego środowiska.  Wersje [_dupenv_s —, _wdupenv_s —](dupenv-s-wdupenv-s.md) który przydzielić pamięci z [_malloc_dbg —](malloc-dbg.md) o podanie dodatkowych informacji debugowania.

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
Bufor do przechowywania wartość zmiennej.

*numberOfElements*<br/>
Rozmiar *buforu*.

*nazwa_zmiennej*<br/>
Nazwa zmiennej środowiskowej.

*blockType*<br/>
Żądany typ bloku pamięci: **_client_block —** lub **_normal_block —**.

*Nazwa pliku*<br/>
Wskaźnik do nazwy pliku źródłowego lub **NULL**.

*numer wiersza*<br/>
Numer wiersza na pliku źródłowego lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia, kod błędu w przypadku awarii.

Te funkcje walidację ich parametrów; Jeśli *buforu* lub *nazwa_zmiennej* jest **NULL**, zgodnie z opisem w wywołaniu program obsługi nieprawidłowych parametrów [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, Ustaw funkcje **errno** do **einval —** i zwracać **einval —**.

Jeśli te funkcje nie może przydzielić wystarczającej ilości pamięci, sami ustawiają *buforu* do **NULL** i *numberOfElements* 0 i powrotu **enomem —**.

## <a name="remarks"></a>Uwagi

**_Dupenv_s_dbg —** i **_wdupenv_s_dbg —** funkcje są takie same jak **_dupenv_s —** i **_wdupenv_s —** z wyjątkiem tego, kiedy **_DEBUG** jest zdefiniowany, te funkcje przy użyciu wersji debugowania [— funkcja malloc](malloc.md), [_malloc_dbg —](malloc-dbg.md), można przydzielić pamięci dla wartości zmiennej środowiskowej. Aby uzyskać informacje dotyczące debugowania funkcji **_malloc_dbg —**, zobacz [_malloc_dbg —](malloc-dbg.md).

Nie trzeba jawnie wywołana w większości przypadków te funkcje. Zamiast tego można określić flagę **_crtdbg_map_alloc —**. Gdy **_crtdbg_map_alloc —** jest zdefiniowany, wywołań **_dupenv_s —** i **_wdupenv_s —** są mapowane ponownie do **_dupenv_s_dbg —** i **_wdupenv_s_dbg —** odpowiednio z *blockType* ustawioną **_normal_block —**. W związku z tym nie trzeba jawnie wywoływać te funkcje, chyba że chcesz oznaczyć bloki sterty jako **_client_block —**. Aby uzyskać więcej informacji o typach bloku, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
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
