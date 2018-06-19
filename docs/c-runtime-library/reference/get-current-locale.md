---
title: _get_current_locale — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_current_locale
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
- get_current_locale
- __get_current_locale
- _get_current_locale
dev_langs:
- C++
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c658d960953bea2890202bebe280d46dd3407d63
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396943"
---
# <a name="getcurrentlocale"></a>_get_current_locale

Pobiera obiekt ustawień regionalnych reprezentujący bieżące ustawienia regionalne.

## <a name="syntax"></a>Składnia

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>Wartość zwracana

Obiekt ustawień regionalnych reprezentujący bieżące ustawienia regionalne.

## <a name="remarks"></a>Uwagi

**_Get_current_locale —** funkcja pobiera aktualnie ustawione ustawień regionalnych dla wątku i zwraca obiekt ustawień regionalnych reprezentujący ustawień regionalnych.

Poprzednia nazwa ta funkcja **__get_current_locale —** (z dwoma podkreśleniami wiodące) jest przestarzała.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_current_locale**|\<locale.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
