---
title: _isctype, iswctype, _isctype_l, _iswctype_l
ms.date: 4/2/2020
api_name:
- _isctype_l
- iswctype
- _iswctype_l
- _isctype
- _o__isctype
- _o__isctype_l
- _o__iswctype_l
- _o_iswctype
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswctype
- _isctype
- _isctype_l
- _iswctype
- isctype
- iswctype_l
- isctype_l
- _iswctype_l
helpviewer_keywords:
- isctype_l function
- iswctype_l function
- iswctype function
- _isctype function
- _isctype_l function
- _iswctype_l function
- isctype function
- _iswctype function
ms.assetid: cf7509b7-12fc-4d95-8140-ad2eb98173d3
ms.openlocfilehash: 5beedd8a5da6848fc8c43ab1a27ee52402fe394e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343851"
---
# <a name="_isctype-iswctype-_isctype_l-_iswctype_l"></a>_isctype, iswctype, _isctype_l, _iswctype_l

Testy *c* dla właściwości ctype określone przez argument *desc.* Dla każdej prawidłowej wartości *desc*istnieje równoważna procedura klasyfikacji szerokich znaków.

## <a name="syntax"></a>Składnia

```C
int _isctype(
   int c,
   _ctype_t desc
);
int _isctype_l(
   int c,
   _ctype_t desc,
   _locale_t locale
);
int iswctype(
   wint_t c,
   wctype_t desc
);
int _iswctype_l(
   wint_t c,
   wctype_t desc,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Całkowita ć do przetestowania.

*desc*<br/>
Właściwość do przetestowania. Jest to zwykle pobierane przy użyciu ctype lub [wctype](wctype.md).

*Ustawień regionalnych*<br/>
Ustawienia regionalne, które mają być używane dla wszystkich testów zależnych od ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

**_isctype** i **iswctype** zwracają wartość niezerową, jeśli *c* ma właściwość określoną przez *desc* w bieżącym otoczeniu lub 0, jeśli nie. Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że używają ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych dla ich zachowania zależnego od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Zachowanie **_isctype** i **_isctype_l** jest niezdefiniowane, jeśli *c* nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy biblioteka CRT debugowania jest używana i *c* nie jest jedną z tych wartości, funkcje podnieść potwierdzenia.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|Nie dotyczy|**_isctype**|Nie dotyczy|**_iswctype**|
|Nie dotyczy|**_isctype_l**|Nie dotyczy|**_iswctype_l**|

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_isctype**|\<ctype.h>|
|**iswctype**|\<ctype.h> lub \<wchar.h>|
|**_isctype_l**|\<ctype.h>|
|**_iswctype_l**|\<ctype.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
