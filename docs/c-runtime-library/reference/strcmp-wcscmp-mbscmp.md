---
title: strcmp —, wcscmp —, _mbscmp — _mbscmp_l
ms.date: 01/22/2019
apiname:
- wcscmp
- _mbscmp
- _mbscmp_l
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
ms.openlocfilehash: dae5e04809ac7312097cb418ab5ffd561fdbd1d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62354226"
---
# <a name="strcmp-wcscmp-mbscmp-mbscmpl"></a>strcmp —, wcscmp —, _mbscmp — _mbscmp_l

Porównywanie ciągów.

> [!IMPORTANT]
> **_mbscmp —** i **_mbscmp_l** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciągi zakończony wartością null do porównania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana dla każdego z tych funkcji określa numerem porządkowym relacji *ciąg1* do *ciąg2*.

|Wartość|Relacja ciąg1 do ciąg2|
|-----------|----------------------------------------|
|< 0|*ciąg1* jest mniejsza niż *ciąg2*|
|0|*ciąg1* jest taka sama jak *ciąg2*|
|> 0|*ciąg1* jest większa niż *ciąg2*|

Na błąd sprawdzania poprawności parametru **_mbscmp —** i **_mbscmp_l** zwracają **_NLSCMPERROR**, który jest zdefiniowany w \<string.h > i \< mbstring.h >.

## <a name="remarks"></a>Uwagi

**Strcmp —** funkcja wykonuje porównanie porządkowe *ciąg1* i *ciąg2* i zwraca wartość wskazującą, ich relacje. **wcscmp —** i **_mbscmp —** odpowiednio są wersjami znaków dwubajtowych i znaków wielobajtowych **strcmp —**. **_mbscmp —** rozpoznaje sekwencje znaków wielobajtowych według bieżącej strony kodowe wielobajtowe i zwraca **_NLSCMPERROR** w przypadku błędu. **_mbscmp_l** ma takie samo zachowanie, ale używa przekazanego parametru ustawień regionalnych, zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [stron kodowych](../../c-runtime-library/code-pages.md). Ponadto jeśli *ciąg1* lub *ciąg2* jest pustym wskaźnikiem, **_mbscmp —** wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **_mbscmp —** i **_mbscmp_l** zwracają **_NLSCMPERROR** i ustaw **errno** do **EINVAL** . **strcmp —** i **wcscmp —** nie sprawdzają poprawność swoich parametrów. Funkcje te zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp —**|**strcmp**|**_mbscmp**|**wcscmp —**|

**Strcmp —** funkcje różnią się od **strcoll —** funkcje, w tym **strcmp —** porównania są porządkowe i są niezależne od ustawień regionalnych. **strcoll —** leksykograficznie porównuje ciągi przy użyciu **LC_COLLATE** kategorii bieżących ustawień regionalnych. Aby uzyskać więcej informacji na temat **LC_COLLATE** kategorii, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md).

W ustawieniach regionalnych "języka C" kolejność znaków w zestawie znaków (zestaw znaków ASCII) jest taka sama jak kolejnością znaków leksykograficznych. Jednak w innych lokalizacjach kolejność znaków w zestawie znaków mogą się różnić od kolejności leksykograficznej. Na przykład w niektórych ustawień regionalnych Europejskich, znaku "" (wartość 0x61) pochodzi przed znakiem "ź" (wartość 0xE4) w zestawie znaków, ale znak "ź" pochodzi przed znakiem "" leksykograficznie.

W lokalizacjach, w których zestaw znaków i kolejnością znaków leksykograficznych różnią się, można użyć **strcoll —** zamiast **strcmp —** leksykograficznych porównywania ciągów. Alternatywnie, można użyć **strxfrm —** na oryginalnym ciągi, a następnie użyj **strcmp —** na ciągi wynikowe.

**Strcmp —** funkcji jest rozróżniana wielkość liter. **\_stricmp —**,  **\_wcsicmp —**, i  **\_mbsicmp —** porównywania ciągów znaków po przekonwertowaniu ich pierwszym na małe litery formularzy. Dwa ciągi zawierające znaki znajdujące się między "Z" i "" w tabeli kodów ASCII ('[','\\","] "," ^ ","_"i"\`') porównać różnie, w zależności od ich przypadku. Na przykład dwa ciągi "ABCDE" i "ABCD ^" porównują w jedna stronę, jeśli wynikiem porównania jest pisana małymi literami ("abcde" > "abcd ^") i w drugą stronę ("ABCDE" < "ABCD ^"), jeśli wynikiem porównania jest wielką literą.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strcmp**|\<string.h>|
|**wcscmp —**|\<Włącz String.h > lub \<wchar.h >|
|**_mbscmp**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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
