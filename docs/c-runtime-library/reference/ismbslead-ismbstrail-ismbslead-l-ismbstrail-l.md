---
title: _ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l
ms.date: 11/04/2016
apiname:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
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
- _ismbslead
- ismbs
- ismbslead_l
- _ismbs
- ismbstrail_l
- ismbslead
- _ismbstrail
- _ismbstrail_l
- ismbstrail
- _ismbslead_l
helpviewer_keywords:
- ismbstrail function
- _ismbslead function
- ismbslead function
- ismbslead_l function
- _ismbstrail function
- _ismbslead_l function
- ismbstrail_l function
- _ismbstrail_l function
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
ms.openlocfilehash: 5b4d3f371f4be640cc22a1bdc3d920acf88e2585
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468916"
---
# <a name="ismbslead-ismbstrail-ismbsleadl-ismbstraill"></a>_ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l

Wykonuje testy kontekstowych dla potencjalnych klientów w ciągu w przypadku znaków wielobajtowych bajtów i bajtów dziennika i określa, czy wskaźnik danego podciągu wskazuje na bajt wiodący lub bajt.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _ismbslead(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbstrail(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbslead_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
int _ismbstrail_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Wskaźnik do początku ciągu lub poprzedniego znanych bajt.

*bieżący*<br/>
Wskaźnik na pozycji w ciągu, który ma zostać przetestowana.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_ismbslead —** zwraca wartość -1, jeśli znak jest wiodącym bajtem i **_ismbstrail —** zwraca wartość -1, jeśli znak jest bajt. Jeśli ciągi wejściowe są prawidłowe, ale nie są bajt wiodący lub bajt, te funkcje zwracają wartość zero. Jeśli którykolwiek z argumentów jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **NULL** i ustaw **errno** do **EINVAL**.

## <a name="remarks"></a>Uwagi

**_ismbslead —** i **_ismbstrail —** wolniej niż **_ismbblead** i **_ismbbtrail** wersje ponieważ uwzględniają kontekst ciągu.

Wersje tych funkcji, które mają **_l** sufiksem są identyczne, z tą różnicą, że zachowań zależnych od ustawień regionalnych używają ustawień regionalnych, który jest przekazywany zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_ismbslead —**|\<mbctype.h > lub \<mbstring.h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbstrail —**|\<mbctype.h > lub \<mbstring.h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbslead_l —**|\<mbctype.h > lub \<mbstring.h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbstrail_l —**|\<mbctype.h > lub \<mbstring.h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\* Dla stałych manifestu do warunków badania.

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, procedury](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
