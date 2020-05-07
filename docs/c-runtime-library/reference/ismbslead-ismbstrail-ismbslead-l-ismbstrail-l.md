---
title: _ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l
ms.date: 4/2/2020
api_name:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
- _o__ismbslead
- _o__ismbslead_l
- _o__ismbstrail
- _o__ismbstrail_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 892545ba0ac66604b0ea1c5adcfa32dd64b68973
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919160"
---
# <a name="_ismbslead-_ismbstrail-_ismbslead_l-_ismbstrail_l"></a>_ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l

Wykonuje testy z uwzględnieniem kontekstu dla ciągu znaków wielobajtowych i bajtów wiodących i końcowych oraz określa, czy dany wskaźnik podciągu wskazuje na bajt wiodący lub końcowy.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Wskaźnik na początek ciągu lub poprzedniego znanego bajtu potencjalnego klienta.

*bieżący*<br/>
Wskaźnik do pozycji w ciągu, który ma być testowany.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_ismbslead** zwraca wartość-1, jeśli znak jest bajtem wiodącym, a **_ismbstrail** zwraca wartość-1, jeśli znak jest bajtem końcowym. Jeśli ciągi wejściowe są prawidłowe, ale nie są bajtem wiodącym lub bajtem końcowym, te funkcje zwracają zero. Jeśli jeden z argumentów ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **wartość null** i ustawiają **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

**_ismbslead** i **_ismbstrail** są wolniejsze niż wersje **_ismbblead** i **_ismbbtrail** , ponieważ przyjmują kontekst ciągu do konta.

Wersje tych funkcji, które mają sufiks **_l** są identyczne, z tą różnicą, że dla zachowania zależnego od ustawień regionalnych korzystają z przekazaną przez użytkownika ustawień regionalnych zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_ismbslead**|\<Mbctype. h> lub \<mbstring. h>|\<CType. h>, * \<Limits. h> \<, STDLIB. h>|
|**_ismbstrail**|\<Mbctype. h> lub \<mbstring. h>|\<CType. h>, * \<Limits. h> \<, STDLIB. h>|
|**_ismbslead_l**|\<Mbctype. h> lub \<mbstring. h>|\<CType. h>, * \<Limits. h> \<, STDLIB. h>|
|**_ismbstrail_l**|\<Mbctype. h> lub \<mbstring. h>|\<CType. h>, * \<Limits. h> \<, STDLIB. h>|

\*Dla stałych manifestu dla warunków testowych.

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Procedury _ismbc](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
