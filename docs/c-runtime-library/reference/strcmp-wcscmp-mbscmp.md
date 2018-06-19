---
title: strcmp —, wcscmp —, _mbscmp — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcscmp
- _mbscmp
- strcmp
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _mbscmp
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
dev_langs:
- C++
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df2168da257c6d1d07cff6400122830da60b5fef
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417448"
---
# <a name="strcmp-wcscmp-mbscmp"></a>strcmp, wcscmp, _mbscmp

Porównywanie ciągów.

> [!IMPORTANT]
> **_mbscmp —** nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int strcmp(
   const char *string1,
   const char *string2
);
int wcscmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscmp(
   const unsigned char *string1,
   const unsigned char *string2
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi zakończone wartością null do porównania.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana dla każdej z tych funkcji wskazuje stosunek liczby porządkowej *ciąg1* do *ciąg2*.

|Wartość|Relacja ciąg1 do ciąg2|
|-----------|----------------------------------------|
|< 0|*ciąg1* jest mniejsza niż *ciąg2*|
|0|*ciąg1* jest taka sama jak *ciąg2*|
|> 0|*ciąg1* jest większa niż *ciąg2*|

Parametr błędu sprawdzania poprawności **_mbscmp —** zwraca **_NLSCMPERROR**, która jest zdefiniowana w \<string.h > i \<mbstring.h >.

## <a name="remarks"></a>Uwagi

**Strcmp —** funkcja przeprowadza porównanie liczby porządkowej *ciąg1* i *ciąg2* i zwraca wartość wskazującą, ich relacji. **wcscmp —** i **_mbscmp —** są odpowiednio znaków dwubajtowych i znaków wielobajtowych wersje **strcmp —**. **_mbscmp —** rozpoznaje wielobajtowych sekwencji znaków zgodnie z bieżącej strony kodowe wielobajtowe i zwraca **_NLSCMPERROR** w przypadku wystąpienia błędu. Aby uzyskać więcej informacji, zobacz [stron kodowych](../../c-runtime-library/code-pages.md). Ponadto jeśli *ciąg1* lub *ciąg2* wskaźnika o wartości null, jest **_mbscmp —** wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **_mbscmp —** zwraca **_NLSCMPERROR** i ustawia **errno** do **einval —**. **strcmp —** i **wcscmp —** nie weryfikują ich parametrów. Te trzy funkcje działają tak samo w przeciwnym razie wartość.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp —**|**strcmp**|**_mbscmp —**|**wcscmp —**|

**Strcmp —** funkcji różnią się od **strcoll —** funkcje, w tym **strcmp —** porównania są porządkowej i są niezależne od ustawień regionalnych. **strcoll —** lexicographically porównuje ciągi za pomocą **lc_collate —** kategorii bieżące ustawienia regionalne. Aby uzyskać więcej informacji na temat **lc_collate —** kategorii, zobacz [setlocale, _wsetlocale —](setlocale-wsetlocale.md).

Zgodnie z ustawieniami regionalnymi "C" kolejność znaków w zestawie znaków (zestaw znaków ASCII) jest taka sama jak kolejność lexicographic znaków. Jednak w innych lokalizacjach kolejność znaków w zestawie znaków mogą się różnić od lexicographic kolejności. Na przykład w niektórych lokalizacjach Europejskich, znak "" (wartość 0x61) znajduje się przed znak "ź" (wartość 0xE4) w zestawie znaków, ale przed znakiem "ź" zawiera znak "" lexicographically.

W których zestaw znaków i kolejność znaków lexicographic inne ustawienia regionalne, można użyć **strcoll —** zamiast **strcmp —** lexicographic porównywania ciągów. Alternatywnie można użyć **strxfrm —** na ciągi oryginalny, a następnie użyć **strcmp —** wynikowy ciągów.

**Strcmp —** funkcji jest rozróżniana wielkość liter. **_stricmp —**, **_wcsicmp —**, i **_mbsicmp —** porównywanie ciągów przez pierwszy konwersję na małe litery formularzy. Dwa ciągi, które zawierają znaki, które znajdują się między "Z" i "" w tabeli ASCII ('[','\\","] "," ^ ","_", i"\`") porównania w różny sposób, w zależności od ich przypadku. Na przykład dwa ciągi "ABCDE" i "ABCD ^" porównania jedną z metod, jeśli jest to mała litera ("abcde" > "abcd ^") i w inny sposób ("ABCDE" < "ABCD ^"), jeśli wynikiem porównania jest wielkie litery.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strcmp**|<string.h>|
|**wcscmp —**|< string.h > lub < wchar.h >|
|**_mbscmp —**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_strcmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof (tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
