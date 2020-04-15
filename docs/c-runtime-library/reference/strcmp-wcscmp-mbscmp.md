---
title: strcmp, wcscmp, _mbscmp, _mbscmp_l
ms.date: 4/2/2020
api_name:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
- _o__mbscmp
- _o__mbscmp_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscmp
- _mbscmp_l
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- _mbscmp_l function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
ms.openlocfilehash: 16bb294f7bbdc0b95b59b845d7b714f823f9d962
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357285"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp, wcscmp, _mbscmp, _mbscmp_l

Porównaj ciągi.

> [!IMPORTANT]
> **_mbscmp** i **_mbscmp_l** nie mogą być używane w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
int _mbscmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi zakończone wartością null do porównania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwracana wartość dla każdej z tych funkcji wskazuje relację porządkową *ciągu1* do *ciągu2*.

|Wartość|Relacja ciągu1 do ciągu2|
|-----------|----------------------------------------|
|< 0|*ciąg1* jest mniejszy niż *ciąg2*|
|0|*string1* jest identyczny z *string2*|
|> 0|*ciąg1* jest większy niż *ciąg2*|

W sprawie błędu sprawdzania poprawności parametrów **_mbscmp** i **_mbscmp_l** zwracają **_NLSCMPERROR** \<, który jest zdefiniowany \<w> string.h i mbstring.h>.

## <a name="remarks"></a>Uwagi

Funkcja **strcmp** wykonuje porównanie porządkowe *string1* i *string2* i zwraca wartość, która wskazuje ich relacji. **wcscmp** i **_mbscmp** są, odpowiednio, szerokoznakowymi i wielobajtowymi znakami **wersji strcmp**. **_mbscmp** rozpoznaje sekwencje znaków wielobajtowych zgodnie z bieżącą wielobajtową stroną kodową i zwraca **_NLSCMPERROR** na błąd. **_mbscmp_l** ma takie samo zachowanie, ale używa parametru ustawień regionalnych, który jest przekazywany zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Strony kodowe](../../c-runtime-library/code-pages.md). Ponadto jeśli *string1* lub *string2* jest wskaźnikiem zerowym, **_mbscmp** wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, **_mbscmp** i **_mbscmp_l** zwrócić **_NLSCMPERROR** i ustawić **errno** na **EINVAL**. **strcmp** i **wcscmp** nie weryfikują swoich parametrów. Te funkcje zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**Strcmp**|**_mbscmp**|**wcscmp**|

Funkcje **strcmp** różnią się od funkcji **strcoll** w tym **strcmp** porównania są porządkowe i nie są dotknięte ustawienia regionalne. **strcoll** porównuje ciągi leksykograficznie przy użyciu **LC_COLLATE** kategorii bieżących ustawień regionalnych. Aby uzyskać więcej informacji na temat **kategorii LC_COLLATE,** zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md).

W ustawieniach regionalnych "C" kolejność znaków w zestawie znaków (zestaw znaków ASCII) jest taka sama jak kolejność znaków leksykograficznych. Jednak w innych ustawieniach regionalnych kolejność znaków w zestawie znaków może różnić się od kolejności leksykograficznej. Na przykład w niektórych europejskich ustawieniach regionalnych znak "a" (wartość 0x61) pojawia się przed znakiem "ä" (wartość 0xE4) w zestawie znaków, ale znak "ä" pojawia się przed znakiem "a" leksykograficznie.

W ustawieniach regionalnych, dla których zestaw znaków i kolejność znaków leksykograficznych różnią się, można użyć **strcoll** zamiast **strcmp** do porównania leksykograficznego ciągów. Alternatywnie można użyć **strxfrm** na oryginalnych ciągów, a następnie użyć **strcmp** na ciągi wynikowe.

W **funkcjach strcmp** rozróżniana jest wielkość liter. stricmp , ** \_wcsicmp**i ** \_mbsicmp porównują** ciągi, konwertując je najpierw na ich małe litery. ** \_** Dwa ciągi zawierające znaki znajdujące się między "Z" i "a" w tabeli ASCII ('[', '\\',\`']', '^', '_', '_' i ' ') porównują się inaczej, w zależności od ich przypadku. Na przykład dwa ciągi "ABCDE" i "ABCD^" porównują jeden ze sposobów, jeśli porównanie jest małe ("abcde" > "abcd^") i w drugą stronę ("ABCDE" < "ABCD^"), jeśli porównanie jest wielkie litery.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Strcmp**|\<string.h>|
|**wcscmp**|\<string.h> lub \<wchar.h>|
|**_mbscmp**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
