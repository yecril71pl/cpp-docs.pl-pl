---
title: _strnicmp —, _wcsnicmp —, _mbsnicmp —, _strnicmp_l —, _wcsnicmp_l —, _mbsnicmp_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wcsnicmp
- _strnicmp_l
- _wcsnicmp_l
- _strnicmp
- _mbsnicmp
- _mbsnicmp_l
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wcsnicmp_l
- _strnicmp
- _ftcsnicmp
- mbsnicmp_l
- _ftcsncicmp
- mbsnicmp
- _tcsncicmp
- _mbsnicmp
- _tcsnicmp
- strnicmp_l
- _wcsnicmp
- _wcsnicmp_l
- CORECRT_WSTRING/_wcsnicmp
- CORECRT_WSTRING/_wcsnicmp_l
- string/_strnicmp
- string/_strnicmp_l
dev_langs:
- C++
helpviewer_keywords:
- tcsnicmp function
- _tcsncicmp function
- _mbsnicmp_l function
- mbsnicmp_l function
- wcsnicmp_l function
- wcsnicmp function
- string comparison [C++], lowercase
- ftcsnicmp function
- strnicmp_l function
- strncmp function
- _strnicmp function
- strings [C++], comparing characters of
- _wcsnicmp_l function
- tcsncicmp function
- string comparison [C++], strncmp function
- _mbsnicmp function
- ftcsncicmp function
- _tcsnicmp function
- _ftcsncicmp function
- _strnicmp_l function
- _ftcsnicmp function
- characters [C++], comparing
- mbsnicmp function
- _wcsnicmp function
ms.assetid: df6e5037-4039-4c85-a0a6-21d4ef513966
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0da454b2b980be3565ee27fde4ee14d7eadd42fb
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313633"
---
# <a name="strnicmp-wcsnicmp-mbsnicmp-strnicmpl-wcsnicmpl-mbsnicmpl"></a>_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l
Porównuje określoną liczbę znaków z dwóch ciągów bez uwzględniania wielkości liter.

> [!IMPORTANT]
> **_mbsnicmp —** i **_mbsnicmp_l —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _strnicmp(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsnicmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsnicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strnicmp_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsnicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count,
   _locale_t locale
);
int _mbsnicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi zakończony wartością null do porównania.

*Liczba*<br/>
Liczba znaków do porównania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Określa relację pomiędzy podciągami, w następujący sposób.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* podciąg ma mniej niż *ciąg2* podciąg.|
|0|*ciąg1* podciągu jest taka sama jak *ciąg2* podciąg.|
|> 0|*ciąg1* podciągu jest większa niż *ciąg2* podciąg.|

Na parametr błąd sprawdzania poprawności, te funkcje zwracają **_NLSCMPERROR**, który jest zdefiniowany w \<string.h > i \<mbstring.h >.

## <a name="remarks"></a>Uwagi

**_Strnicmp —** funkcja ordinally porównuje, co najwyżej, pierwsze *liczba* znaków *ciąg1* i *ciąg2*. Porównanie jest wykonywane bez uwzględniania wielkości liter, dokonując przekonwertowania na małe litery, każdy znak. **_strnicmp —** jest wersją uwzględniającą wielkości **strncmp —**. Porównanie kończy się po osiągnięciu kończącego znaku null albo w ciągu przed *liczba* znaki są porównywane. Jeśli ciągi są równe gdy kończący znak null jest osiągany w każdym ciągu przed *liczba* znaki są porównywane, krótszy ciąg jest mniejszy.

Znaków 91 96 w tabeli kodów ASCII ('[','\\","] "," ^ ","_"i"\`") oceny jako mniej niż dowolny znaku alfabetyczny. Ta kolejność jest taka sama jak w przypadku **stricmp —**.

**_wcsnicmp —** i **_mbsnicmp —** są wersjami znaków dwubajtowych i znaków wielobajtowych **_strnicmp —**. Argumenty **_wcsnicmp —** są znakami dwubajtowymi ciągów; te z **_mbsnicmp —** są ciągami znaków wielobajtowych. **_mbsnicmp —** rozpoznaje sekwencje znaków wielobajtowych według bieżącej strony kodowe wielobajtowe i zwraca **_NLSCMPERROR** w przypadku błędu. Aby uzyskać więcej informacji, zobacz [stron kodowych](../../c-runtime-library/code-pages.md). Te trzy funkcje zachowują się identycznie. Te funkcje zależą od ustawień regionalnych — wersje, które nie mają **_l** sufiks używają bieżących ustawień regionalnych dla swoich zachowań zależnych od ustawień regionalnych; wersje, które mają **_l** sufiks Zamiast tego użyć *ustawień regionalnych* który jest przekazywany w. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Wszystkie te funkcje sprawdzają poprawność swoich parametrów. Jeśli *ciąg1* lub *ciąg2* jest pustym wskaźnikiem, wywoływany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **_NLSCMPERROR** i ustaw **errno** do **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicmp —**|**_strnicmp**|**_mbsnicmp —**|**_wcsnicmp**|
|**_tcsnicmp —**|**_strnicmp**|**_mbsnbicmp —**|**_wcsnicmp**|
|**_tcsncicmp_l**|**_strnicmp_l**|**_mbsnicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strnicmp —**, **_strnicmp_l —**|\<string.h>|
|**_wcsnicmp —**, **_wcsnicmp_l —**|\<Włącz String.h > lub \<wchar.h >|
|**_mbsnicmp —**, **_mbsnicmp_l —**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [strncmp —](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
