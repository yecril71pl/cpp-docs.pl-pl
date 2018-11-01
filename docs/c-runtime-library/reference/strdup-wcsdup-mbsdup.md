---
title: _strdup, _wcsdup, _mbsdup
ms.date: 11/04/2016
apiname:
- _strdup
- _mbsdup
- _wcsdup
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsdup
- mbsdup
- _mbsdup
- _strdup
- _ftcsdup
- _wcsdup
helpviewer_keywords:
- wcsdup function
- ftcsdup function
- _ftcsdup function
- mbsdup function
- strdup function
- _strdup function
- _wcsdup function
- copying strings
- duplicating strings
- strings [C++], copying
- _mbsdup function
- strings [C++], duplicating
- tcsdup function
- _tcsdup function
ms.assetid: 8604f8bb-95e9-45d3-93ef-20397ebf247a
ms.openlocfilehash: 094843fdb1432aa58ec04b3b4e39ac8861b928ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461519"
---
# <a name="strdup-wcsdup-mbsdup"></a>_strdup, _wcsdup, _mbsdup

Ciągi duplikaty.

> [!IMPORTANT]
> **_mbsdup —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *_strdup(
   const char *strSource
);
wchar_t *_wcsdup(
   const wchar_t *strSource
);
unsigned char *_mbsdup(
   const unsigned char *strSource
);
```

### <a name="parameters"></a>Parametry

*strSource*<br/>
Ciąg źródłowy zakończony wartością null.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do lokalizacji przechowywania skopiowany ciąg lub **NULL** Jeśli nie można przydzielić pamięci masowej.

## <a name="remarks"></a>Uwagi

**_Strdup —** wywołaniach funkcji [— funkcja malloc](malloc.md) przydzielić miejsce do magazynowania dla kopię *strSource* , a następnie kopiuje *strSource* do Przydzielone miejsce.

**_wcsdup —** i **_mbsdup —** są wersjami znaków dwubajtowych i znaków wielobajtowych **_strdup —**. Argumenty i wartość zwracana przez **_wcsdup —** są znakami dwubajtowymi ciągów; te z **_mbsdup —** są ciągami znaków wielobajtowych. Te trzy funkcje zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup —**|**_strdup**|**_mbsdup —**|**_wcsdup**|

Ponieważ **_strdup —** wywołania **— funkcja malloc** do przydzielenia miejsca do magazynowania kopii *strSource*, jest dobrym rozwiązaniem zawsze wydania tej pamięci przez wywołanie metody [bezpłatne](free.md) rutynowych we wskaźniku, który jest zwracany przez wywołanie metody **_strdup —**.

Jeśli **_DEBUG** i **_CRTDBG_MAP_ALLOC** są zdefiniowane, **_strdup —** i **_wcsdup —** są zastępowane przez wywołania **_strdup_dbg —**  i **_wcsdup_dbg —** aby umożliwić debugowanie alokacji pamięci. Aby uzyskać więcej informacji, zobacz [_strdup_dbg —, _wcsdup_dbg —](strdup-dbg-wcsdup-dbg.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strdup**|\<string.h>|
|**_wcsdup**|\<Włącz String.h > lub \<wchar.h >|
|**_mbsdup —**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strdup.c

#include <string.h>
#include <stdio.h>

int main( void )
{
   char buffer[] = "This is the buffer text";
   char *newstring;
   printf( "Original: %s\n", buffer );
   newstring = _strdup( buffer );
   printf( "Copy:     %s\n", newstring );
   free( newstring );
}
```

```Output
Original: This is the buffer text
Copy:     This is the buffer text
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
