---
title: "_get_current_locale — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_current_locale
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
dev_langs: C++
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0ebee381e71e55f564d97dbf7ced6fe599de3728
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="getcurrentlocale"></a>_get_current_locale
Pobiera obiekt ustawień regionalnych reprezentujący bieżące ustawienia regionalne.  
  
## <a name="syntax"></a>Składnia  
  
```  
_locale_t _get_current_locale(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt ustawień regionalnych reprezentujący bieżące ustawienia regionalne.  
  
## <a name="remarks"></a>Uwagi  
 `_get_current_locale` Funkcja pobiera aktualnie ustawione ustawień regionalnych dla wątku i zwraca obiekt ustawień regionalnych reprezentujący ustawień regionalnych.  
  
 Poprzednia nazwa tej funkcji `__get_current_locale` (z dwoma podkreśleniami wiodące) jest przestarzała.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_get_current_locale`|\<Locale.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../../c-runtime-library/reference/free-locale.md)