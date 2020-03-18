---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 11/04/2016
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _mbsnbicmp_l
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
ms.openlocfilehash: c7a4d5def115101c9f3fbd6c53d649ab5b122f1c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442837"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp, _mbsnbicmp_l

Porównuje **n** bajtów dwóch ciągów znaków wielobajtowych i ignoruje wielkość liter.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciągi zakończone wartością null do porównania.

*count*<br/>
Liczba bajtów do porównania.

## <a name="return-value"></a>Wartość zwrócona

Wartość zwracana określa relację między podciągami.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* podciągu krótszy niż *ciąg2* podciąg.|
|0|*ciąg1* podciąg identyczny z podciągiem *ciąg2* .|
|> 0|*ciąg1* podciąg jest większy niż *ciąg2* podciąg.|

W przypadku błędu, **_mbsnbicmp** zwraca **_NLSCMPERROR**, który jest zdefiniowany w String. h i mbstring. h.

## <a name="remarks"></a>Uwagi

Funkcja **_mbsnbicmp** wykonuje porównanie porządkowe *dla pierwszych bajtów* z wartości *ciąg1* i *ciąg2*. Porównanie jest wykonywane przez konwersję każdego znaku na małe litery; [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) to wersja **_mbsnbicmp**z uwzględnieniem wielkości liter. Porównanie kończy się, jeśli kończący znak null zostanie osiągnięty w dowolnym ciągu przed porównaniem znaków *Count* . Jeśli ciągi są równe, gdy zostanie osiągnięty kończący znak null w dowolnym ciągu przed porównaniem znaków *Count* , krótszy ciąg jest mniejszy.

**_mbsnbicmp** jest podobna do [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), z tą różnicą, że porównuje ciągi do *liczby* bajtów zamiast znaków.

Dwa ciągi zawierające znaki znajdujące się między "Z" i "a" w tabeli ASCII ("[", "\\", "]", "^", "_" i "\`") różnią się w zależności od ich wielkości liter. Na przykład dwa ciągi "ABCDe" i "ABCD ^" porównują jeden sposób, jeśli porównanie jest małe ("abcde" > "abcd ^") i drugi sposób ("ABCDe" < "ABCD ^"), jeśli jest to wielkie litery.

**_mbsnbicmp** rozpoznaje sekwencje znaków wielobajtowych zgodnie z aktualnie używaną [stroną kodową](../../c-runtime-library/code-pages.md) . Bieżące ustawienie regionalne nie ma na nie wpływ.

Jeśli *ciąg1* lub *ciąg2* jest wskaźnikiem o wartości null, **_mbsnbicmp** wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **_NLSCMPERROR** i ustawia **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
