---
title: _get_current_locale
ms.date: 11/04/2016
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
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
ms.openlocfilehash: 87c30ee701d8f7d3a89a0aa61ba18a7f854bc9b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332297"
---
# <a name="getcurrentlocale"></a>_get_current_locale

Pobiera obiekt ustawień regionalnych reprezentujący bieżących ustawień regionalnych.

## <a name="syntax"></a>Składnia

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>Wartość zwracana

Obiekt ustawień regionalnych reprezentujący bieżących ustawień regionalnych.

## <a name="remarks"></a>Uwagi

**_Get_current_locale —** funkcja pobiera aktualnie ustawione ustawienia regionalne dla wątku i zwraca obiekt ustawień regionalnych reprezentujący ustawień regionalnych.

Poprzednia nazwa tej funkcji **__get_current_locale —** (z dwoma wiodącymi podkreśleniami) jest przestarzała.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_current_locale**|\<locale.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
