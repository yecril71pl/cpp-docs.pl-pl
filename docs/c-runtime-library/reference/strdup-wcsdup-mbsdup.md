---
title: _strdup, _wcsdup, _mbsdup
ms.date: 4/2/2020
api_name:
- _strdup
- _mbsdup
- _wcsdup
- _o__strdup
- _o__wcsdup
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 7ad28633844c49ce5b86c8f71f4502c62eba1216
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359694"
---
# <a name="_strdup-_wcsdup-_mbsdup"></a>_strdup, _wcsdup, _mbsdup

Duplikuje ciągi.

> [!IMPORTANT]
> **_mbsdup** nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*strSource (źródło usług strSource)*<br/>
Ciąg źródłowy zakończony z wartością null.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do lokalizacji magazynu dla skopiowanego ciągu lub **NULL,** jeśli nie można zaalokować magazynu.

## <a name="remarks"></a>Uwagi

Funkcja **_strdup** wywołuje [malloc,](malloc.md) aby przydzielić miejsce do magazynowania dla kopii *strSource,* a następnie kopiuje *strSource* do przydzielonego miejsca.

**_wcsdup** i **_mbsdup** są wersjami **_strdup**o szerokich i wielobajtowych znakach. Argumenty i zwracana wartość **_wcsdup** są ciągami znaków o szerokich znakach; **_mbsdup** są ciągami znaków wielobajtowych. Te trzy funkcje zachowują się identycznie inaczej.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup**|**_strdup**|**_mbsdup**|**_wcsdup**|

Ponieważ **_strdup** wywoła **malloc,** aby przydzielić miejsce do przechowywania kopii *strSource,* dobrą praktyką jest zawsze zwolnić tę pamięć, wywołując [bezpłatną](free.md) procedurę na wskaźniku, który jest zwracany przez wywołanie **_strdup**.

Jeśli **zdefiniowano _DEBUG** i **_CRTDBG_MAP_ALLOC,** **_strdup** i **_wcsdup** są zastępowane przez wywołania **_strdup_dbg** i **_wcsdup_dbg,** aby umożliwić debugowanie alokacji pamięci. Aby uzyskać więcej informacji, zobacz [_strdup_dbg _wcsdup_dbg](strdup-dbg-wcsdup-dbg.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strdup**|\<string.h>|
|**_wcsdup**|\<string.h> lub \<wchar.h>|
|**_mbsdup**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

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
