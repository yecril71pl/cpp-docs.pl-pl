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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 805e355fe12cb2f7ead6180edd45ad0748570141
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920379"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp, wcscmp, _mbscmp, _mbscmp_l

Porównaj ciągi.

> [!IMPORTANT]
> **_mbscmp** i **_mbscmp_l** nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana dla każdej z tych funkcji wskazuje liczbę porządkową od *ciąg1* do *ciąg2*.

|Wartość|Relacja ciąg1 do ciąg2|
|-----------|----------------------------------------|
|< 0|*ciąg1* jest krótszy niż *ciąg2*|
|0|*ciąg1* jest identyczny z *ciąg2*|
|> 0|*ciąg1* jest większy niż *ciąg2*|

W przypadku błędu walidacji parametru **_mbscmp** i **_mbscmp_l** zwracają **_NLSCMPERROR**, który jest zdefiniowany w \<> String. h i \<mbstring. h>.

## <a name="remarks"></a>Uwagi

Funkcja **strcmp** wykonuje porównanie porządkowe *ciąg1* i *ciąg2* i zwraca wartość, która wskazuje ich relację. **wcscmp** i **_mbscmp** są odpowiednio, wersjami szerokich znaków i znaków wielobajtowych **strcmp**. **_mbscmp** rozpoznaje sekwencje znaków wielobajtowych zgodnie z bieżącą stroną kodową wielobajtowego i zwraca **_NLSCMPERROR** w przypadku błędu. **_mbscmp_l** ma takie samo zachowanie, ale używa parametru ustawień regionalnych, który jest przesyłany zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [stronę kodową](../../c-runtime-library/code-pages.md). Ponadto, jeśli *ciąg1* lub *ciąg2* jest wskaźnikiem o wartości null, **_mbscmp** wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **_mbscmp** i **_mbscmp_l** zwrócić **_NLSCMPERROR** i ustawić **errno** na **EINVAL**. **strcmp** i **wcscmp** nie weryfikują ich parametrów. Funkcje te zachowują się identycznie w inny sposób.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

Funkcje **strcmp** różnią się od funkcji **strcoll —** w tym porównań **strcmp** z liczbą porządkową i nie wpływają na ustawienia regionalne. **strcoll —** porównuje ciągi lexicographically przy użyciu kategorii **LC_COLLATE** bieżących ustawień regionalnych. Aby uzyskać więcej informacji o kategorii **LC_COLLATE** , zobacz [setlocaling, _wsetlocale](setlocale-wsetlocale.md).

W ustawieniach regionalnych "C" kolejność znaków w zestawie znaków (zestaw znaków ASCII) jest taka sama jak kolejność znaków leksykograficznych. Jednak w innych ustawieniach regionalnych kolejność znaków w zestawie znaków może różnić się od kolejności leksykograficznych. Na przykład w niektórych europejskich ustawieniach regionalnych znak "a" (wartość 0x61) jest wcześniejszy niż znak "ä" (wartość 0xE4) w zestawie znaków, ale znak "ä" znajduje się przed znakiem "a" lexicographically.

W ustawieniach regionalnych, dla których zestaw znaków i kolejność znaków leksykograficznych są różne, można użyć **strcoll —** zamiast **strcmp** do porównywania ciągów przez leksykograficznych. Alternatywnie możesz użyć **strxfrm** w oryginalnych ciągach, a następnie użyć **strcmp** na ciągach z wynikiem.

W funkcjach **strcmp** jest rozróżniana wielkość liter. stricmp, ** \_wcsicmp**i ** \_mbsicmp** porównują ciągi, przenosząc je najpierw do postaci małych liter. ** \_** Dwa ciągi zawierające znaki, które znajdują się między "z" i "a" w tabeli ASCII ("[", "\\", "]", "^", "_" i "\`"), różnią się w zależności od ich wielkości liter. Na przykład dwa ciągi "ABCDe" i "ABCD ^" porównują jeden sposób, jeśli porównanie jest małe ("abcde" > "abcd ^") i drugi sposób ("ABCDe" < "ABCD ^"), jeśli porównanie ma wielkie litery.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strcmp**|\<> String. h|
|**wcscmp**|\<ciąg. h> lub \<WCHAR. h>|
|**_mbscmp**|\<mbstring. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

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
