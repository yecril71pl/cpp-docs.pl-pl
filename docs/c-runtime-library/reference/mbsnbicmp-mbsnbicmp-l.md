---
title: _mbsnbicmp —, _mbsnbicmp_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
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
apitype: DLLExport
f1_keywords:
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
dev_langs:
- C++
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43c9da102f81654062518ca8e886aab1c49df623
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314966"
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp, _mbsnbicmp_l

Porównuje **n** bajtów znaków wielobajtowych dwa ciągi i ignoruje wielkość liter.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*ciąg1*, *ciąg2*<br/>
Ciągi zakończony wartością null do porównania.

*Liczba*<br/>
Liczba bajtów do porównania.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana określa relację pomiędzy podciągami.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* podciąg mniejszy niż *ciąg2* podciąg.|
|0|*ciąg1* podciąg identyczny z *ciąg2* podciąg.|
|> 0|*ciąg1* podciąg większy niż *ciąg2* podciąg.|

W przypadku błędu **_mbsnbicmp —** zwraca **_NLSCMPERROR**, który jest zdefiniowany w String.h i Mbstring.h.

## <a name="remarks"></a>Uwagi

**_Mbsnbicmp —** funkcja wykonuje porównanie porządkowe, co najwyżej pierwsze *liczba* bajtów *ciąg1* i *ciąg2*. Porównanie jest wykonywane, dokonując przekonwertowania na małe litery; każdy znak [_mbsnbcmp —](mbsnbcmp-mbsnbcmp-l.md) jest rozróżniana wielkość liter wersją **_mbsnbicmp —**. Porównanie kończy się po osiągnięciu kończącego znaku null albo w ciągu przed *liczba* znaki są porównywane. Jeśli ciągi są równe gdy kończący znak null jest osiągany w każdym ciągu przed *liczba* znaki są porównywane, krótszy ciąg jest mniejszy.

**_mbsnbicmp —** przypomina [_mbsnbcmp —](mbsnbcmp-mbsnbcmp-l.md), z tą różnicą, że porównuje ciągi do *liczba* bajtów, a znakami.

Dwa ciągi zawierające znaki znajdujące się między "Z" i "" w tabeli kodów ASCII ('[','\\","] "," ^ ","_"i"\`') porównać różnie, w zależności od ich przypadku. Na przykład dwa ciągi "ABCDE" i "ABCD ^" porównują w jedna stronę, jeśli wynikiem porównania jest pisana małymi literami ("abcde" > "abcd ^") i w drugą stronę ("ABCDE" < "ABCD ^") jeżeli wynik jest dużą literą.

**_mbsnbicmp —** rozpoznaje sekwencje znaków wielobajtowych według [wielobajtowa strona kodowa](../../c-runtime-library/code-pages.md) aktualnie w użyciu. Nie występuje przy bieżących ustawień regionalnych.

Jeśli *ciąg1* lub *ciąg2* jest pustym wskaźnikiem, **_mbsnbicmp —** wywołuje program obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **_NLSCMPERROR** i ustawia **errno** do **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp —**|**_strnicmp**|**_mbsnbicmp —**|**_wcsnicmp**|
|**_tcsnicmp_l —**|**_strnicmp_l**|**_mbsnbicmp_l —**|**_wcsnicmp_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbicmp —**|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_mbsnbcmp —, _mbsnbcmp_l —](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
