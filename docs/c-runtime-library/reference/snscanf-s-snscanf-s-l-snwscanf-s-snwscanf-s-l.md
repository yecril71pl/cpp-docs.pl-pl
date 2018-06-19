---
title: _snscanf_s —, _snscanf_s_l —, _snwscanf_s —, _snwscanf_s_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _snwscanf_s_l
- _snwscanf_s
- _snscanf_s
- _snscanf_s_l
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
- _sntscanf_s
- snscanf_s
- _snwscanf_s_l
- sntscanf_s_l
- snwscanf_s_l
- snwscanf_s
- _snscanf_s
- _snwscanf_s
- snscanf_s_l
- _sntscanf_s_l
- _snscanf_s_l
- sntscanf_s
dev_langs:
- C++
helpviewer_keywords:
- _snscanf_s_l function
- snwscanf_s function
- _snwscanf_s function
- sntscanf_s_l function
- sntscanf_s function
- _snwscanf_s_l function
- _snscanf_s function
- snscanf_s_l function
- strings [C++], reading data from
- _sntscanf_s_l function
- reading data, strings
- snscanf_s function
- strings [C++], reading
- _sntscanf_s function
- snwscanf_s_l function
ms.assetid: 72356653-7362-461a-af73-597b9c0a8094
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08c269d0139767f260c68d07d660ecc818b36cc4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411412"
---
# <a name="snscanfs-snscanfsl-snwscanfs-snwscanfsl"></a>_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l

Odczyty sformatowanych danych o określonej długości ciągu. Są to wersje [_snscanf —, _snscanf_l —, _snwscanf —, _snwscanf_l —](snscanf-snscanf-l-snwscanf-snwscanf-l.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int __cdecl _snscanf_s(
   const char * input,
   size_t length,
   const char * format [, argument_list]
);
int __cdecl _snscanf_s_l(
   const char * input,
   size_t length,
   const char * format,
   locale_t locale [, argument_list]
);
int __cdecl _snwscanf_s(
   const wchar_t * input,
   size_t length,
   const wchar_t * format [, argument_list]
);
int __cdecl _snwscanf_s_l(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   locale_t locale [, argument_list]
);
```

### <a name="parameters"></a>Parametry

*Dane wejściowe*<br/>
Wejściowy ciąg do sprawdzenia.

*długość*<br/>
Liczba znaków zbadać *wejściowych*.

*Format*<br/>
Specyfikatory formatu jeden lub więcej.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

*argument_list*<br/>
Argumenty opcjonalne przypisanie zgodnie z ciągu formatu.

## <a name="return-value"></a>Wartość zwracana

Obie te funkcje zwraca liczbę pól pomyślnie przekonwertowany i przypisane; wartość zwrotna nie zawiera pola, które zostały do odczytu, ale nie są przypisane. Wartość zwracana 0 wskazuje, że nie ma pól zostały przypisane. Wartość zwracana jest **EOF** błędu lub po osiągnięciu końca ciągu przed pierwszym konwersji. Aby uzyskać więcej informacji, zobacz [sscanf_s —, _sscanf_s_l —, swscanf_s —, _swscanf_s_l —](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

Jeśli *wejściowych* lub *format* jest **NULL** wskaźnika, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają **EOF** i ustaw **errno** do **einval —**.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Ta funkcja przypomina **sscanf_s —** z tą różnicą, że zapewnia możliwość określenia stała liczba znaków do sprawdzenia z ciągu wejściowego. Aby uzyskać więcej informacji, zobacz [sscanf_s —, _sscanf_s_l —, swscanf_s —, _swscanf_s_l —](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

Parametr rozmiaru buforu jest wymagany w przypadku znaki pola typu **c**, **C**, **s**, **S**, i **[** . Aby uzyskać więcej informacji, zobacz [scanf — znaki pola typu](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Parametr rozmiaru jest typu **niepodpisane**, a nie **size_t**.

Wersje tych funkcji z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntscanf_s —**|**_snscanf_s**|**_snscanf_s**|**_snwscanf_s**|
|**_sntscanf_s_l —**|**_snscanf_s_l**|**_snscanf_s_l**|**_snwscanf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_snscanf_s —**, **_snscanf_s_l —**|\<stdio.h>|
|**_snwscanf_s —**, **_snwscanf_s_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_snscanf_s.c
// This example scans a string of
// numbers, using both the character
// and wide character secure versions
// of the snscanf function.

#include <stdio.h>

int main( )
{
    char        str1[] = "15 12 14...";
    wchar_t     str2[] = L"15 12 14...";
    char        s1[3];
    wchar_t     s2[3];
    int         i;
    float       fp;

    i = _snscanf_s( str1, 6,  "%s %f", s1, 3, &fp);
    printf_s("_snscanf_s converted %d fields: ", i);
    printf_s("%s and %f\n", s1, fp);

    i = _snwscanf_s( str2, 6,  L"%s %f", s2, 3, &fp);
    wprintf_s(L"_snwscanf_s converted %d fields: ", i);
    wprintf_s(L"%s and %f\n", s2, fp);
}
```

```Output
_snscanf_s converted 2 fields: 15 and 12.000000
_snwscanf_s converted 2 fields: 15 and 12.000000
```

## <a name="see-also"></a>Zobacz także

[scanf, specyfikacje szerokości](../../c-runtime-library/scanf-width-specification.md)<br/>
