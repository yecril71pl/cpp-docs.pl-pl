---
title: _free_locale
ms.date: 4/2/2020
api_name:
- _free_locale
- _o__free_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __free_locale
- free_locale
- _free_locale
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
ms.openlocfilehash: 568e44d731f384a0503420339d716fdfdc81e13a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346044"
---
# <a name="_free_locale"></a>_free_locale

Zwalnia obiekt ustawień regionalnych.

## <a name="syntax"></a>Składnia

```C
void _free_locale(
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Ustawień regionalnych*<br/>
Obiekt ustawień regionalnych do bezpłatnego.

## <a name="remarks"></a>Uwagi

Funkcja **_free_locale** służy do zwalniania obiektu ustawień regionalnych uzyskanego z wywołania **_get_current_locale** lub **_create_locale**.

Poprzednia nazwa tej funkcji, **__free_locale** (z dwoma podkreśleniami wiodącymi) została przestarzała.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|**Procedura**|Wymagany nagłówek|
|---------------|---------------------|
|**_free_locale**|\<>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
