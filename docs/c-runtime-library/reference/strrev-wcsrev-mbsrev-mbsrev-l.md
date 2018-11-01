---
title: _strrev, _wcsrev, _mbsrev, _mbsrev_l
ms.date: 11/04/2016
apiname:
- _wcsrev
- _mbsrev
- _strrev
- _mbsrev_l
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
- _strrev
- _ftcsrev
- _tcsrev
- mbsrev
- mbsrev_l
- _wcsrev_fstrrev
- _mbsrev
helpviewer_keywords:
- _mbsrev_l function
- characters [C++], switching
- _mbsrev function
- strrev function
- _ftcsrev function
- strings [C++], reversing
- wcsrev function
- _strrev function
- mbsrev_l function
- reversing characters in strings
- ftcsrev function
- characters [C++], reversing order
- _wcsrev function
- mbsrev function
- tcsrev function
- _tcsrev function
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
ms.openlocfilehash: 3a35e72875f4166179a119ec6994828302809afb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435564"
---
# <a name="strrev-wcsrev-mbsrev-mbsrevl"></a>_strrev, _wcsrev, _mbsrev, _mbsrev_l

Odwraca znaki ciągu.

> [!IMPORTANT]
> **_mbsrev —** i **_mbsrev_l —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *_strrev(
   char *str
);
wchar_t *_wcsrev(
   wchar_t *str
);
unsigned char *_mbsrev(
   unsigned char *str
);
unsigned char *_mbsrev_l(
   unsigned char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ciąg zakończony znakiem null, aby odwrócić.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do zmienionego ciągu. Zwraca żadnej wartości zarezerwowanej, aby wskazać błąd.

## <a name="remarks"></a>Uwagi

**_Strrev —** funkcja Odwraca kolejność znaków w *str*. Kończący znak null pozostaje na swoim miejscu. **_wcsrev —** i **_mbsrev —** są wersjami znaków dwubajtowych i znaków wielobajtowych **_strrev —**. Argumenty i wartość zwracana przez **_wcsrev —** są znakami dwubajtowymi ciągów; te z **_mbsrev —** są ciągami znaków wielobajtowych. Aby uzyskać **_mbsrev —**, kolejność bajtów w każdym znaku wielobajtowym w *str* nie ulegną zmianie. Te trzy funkcje zachowują się identycznie.

**_mbsrev —** sprawdza poprawność parametrów. Jeśli *ciąg1* lub *ciąg2* jest pustym wskaźnikiem, wywoływany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **_mbsrev —** zwraca **NULL** i ustawia **errno** do **EINVAL**. **_strrev —** i **_wcsrev —** nie sprawdzają poprawność swoich parametrów.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji są identyczne, z tą różnicą, że te, które nie mają **_l** sufiksa używa bieżących ustawień regionalnych i te, które mają **_l** sufiks używają parametru ustawień regionalnych to przekazana. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Funkcje te mogą być podatne na zagrożenia przepełnienia buforu. Przepełnienia buforu może służyć do ataków systemu, ponieważ mogą one spowodować nieuzasadnione podniesienie poziomu uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsrev —**|**_strrev**|**_mbsrev**|**_wcsrev**|
|**n/d**|**n/d**|**_mbsrev_l**|**n/d**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strrev**|\<string.h>|
|**_wcsrev**|\<Włącz String.h > lub \<wchar.h >|
|**_mbsrev —**, **_mbsrev_l —**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strrev.c
// This program checks a string to see
// whether it is a palindrome: that is, whether
// it reads the same forward and backward.
//

#include <string.h>
#include <stdio.h>

int main( void )
{
   char* string = "Able was I ere I saw Elba";
   int result;

   // Reverse string and compare (ignore case):
   result = _stricmp( string, _strrev( _strdup( string ) ) );
   if( result == 0 )
      printf( "The string \"%s\" is a palindrome\n", string );
   else
      printf( "The string \"%s\" is not a palindrome\n", string );
}
```

```Output
The string "Able was I ere I saw Elba" is a palindrome
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
