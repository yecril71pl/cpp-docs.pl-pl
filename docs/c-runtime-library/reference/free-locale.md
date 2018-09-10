---
title: _free_locale — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _free_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __free_locale
- free_locale
- _free_locale
dev_langs:
- C++
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce945499505b7efcaaf010585f27fbfaf42a06b8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103322"
---
# <a name="freelocale"></a>_free_locale

Zwalnia obiektu ustawień regionalnych.

## <a name="syntax"></a>Składnia

```C
void _free_locale(
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Ustawienia regionalne*<br/>
Obiekt ustawień regionalnych do bezpłatnej.

## <a name="remarks"></a>Uwagi

**_Free_locale —** funkcja jest używana w celu zwolnienia obiektu ustawień regionalnych, uzyskany z wywołania **_get_current_locale —** lub **_create_locale**.

Poprzednia nazwa tej funkcji **__free_locale —** (z dwoma wiodącymi podkreśleniami) jest przestarzała.

## <a name="requirements"></a>Wymagania

|**Procedura**|Wymagany nagłówek|
|---------------|---------------------|
|**_free_locale**|\<locale.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_get_current_locale](get-current-locale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
