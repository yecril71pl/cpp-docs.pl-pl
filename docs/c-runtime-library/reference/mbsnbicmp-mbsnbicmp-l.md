---
title: _mbsnbicmp —, _mbsnbicmp_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 07d298a77a5b1f5c20c2fdd004af35da61abdbfc
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp, _mbsnbicmp_l

Porównuje **n** bajtów dwóch znaków wielobajtowych ciągi i ignoruje wielkość liter.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Liczba*<br/>
Liczba bajtów do porównania.

## <a name="return-value"></a>Wartość zwracana

Wartości zwracanej wskazuje relację między podciągów.

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|*ciąg1* podciąg mniej niż *ciąg2* podciąg.|
|0|*ciąg1* podciąg taki sam jak *ciąg2* podciąg.|
|> 0|*ciąg1* podciąg większe *ciąg2* podciąg.|

W przypadku wystąpienia błędu **_mbsnbicmp —** zwraca **_NLSCMPERROR**, która jest zdefiniowana w String.h i Mbstring.h.

## <a name="remarks"></a>Uwagi

**_Mbsnbicmp —** funkcja przeprowadza porównanie liczby porządkowej co najwyżej pierwszego *liczba* bajtów *ciąg1* i *ciąg2*. Porównanie odbywa się za pomocą konwersji na małe litery; każdy znak [_mbsnbcmp —](mbsnbcmp-mbsnbcmp-l.md) jest rozróżniana wielkość liter wersja **_mbsnbicmp —**. Porównanie kończy się po osiągnięciu znak końcowy null w każdym ciągu przed *liczba* znaki są porównywane. Jeśli ciągi są takie same po znak końcowy null osiągnięciu w każdym ciągu przed *liczba* znaki są porównywane, krótszego ciągu jest mniejsza.

**_mbsnbicmp —** jest podobny do [_mbsnbcmp —](mbsnbcmp-mbsnbcmp-l.md), ale do porównywania ciągów *liczba* bajtów zamiast znaków.

Dwa ciągi zawierające znaki znajdujące się między "Z" i "" w tabeli ASCII ('[','\\","] "," ^ ","_", i"\`") porównania w różny sposób, w zależności od ich przypadku. Na przykład dwa ciągi "ABCDE" i "ABCD ^" porównanie jedną z metod, jeśli wynikiem porównania jest małe litery ("abcde" > "abcd ^") i w inny sposób ("ABCDE" < "ABCD ^") jeśli wielkie litery.

**_mbsnbicmp —** rozpoznaje wielobajtowych sekwencji znaków zgodnie z [strony kodowe wielobajtowe](../../c-runtime-library/code-pages.md) obecnie w użyciu. Nie dotyczy on bieżących ustawień regionalnych.

Jeśli dowolny *ciąg1* lub *ciąg2* wskaźnika o wartości null, jest **_mbsnbicmp —** wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca **_NLSCMPERROR** i ustawia **errno** do **einval —**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp —**|**_strnicmp**|**_mbsnbicmp —**|**_wcsnicmp**|
|**_tcsnicmp_l —**|**_strnicmp_l**|**_mbsnbicmp_l —**|**_wcsnicmp_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbicmp —**|<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_mbsnbcmp —, _mbsnbcmp_l —](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
