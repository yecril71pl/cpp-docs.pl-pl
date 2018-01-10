---
title: ___lc_locale_name_func | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: ___lc_locale_name_func
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords: ___lc_locale_name_func
dev_langs: C++
helpviewer_keywords: ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 243fcd75c657125e001e4dc0544e9c315df1bd07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lclocalenamefunc"></a>___lc_locale_name_func
Funkcji CRT wewnętrznej. Pobiera nazwę bieżącego ustawienia regionalne wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
wchar_t** ___lc_locale_name_func(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do ciąg znaków zawierający nazwę bieżącego ustawienia regionalne wątku.  
  
## <a name="remarks"></a>Uwagi  
 `___lc_locale_name_func`jest wewnętrzny funkcji CRT, która jest używana przez inne funkcje CRT można uzyskać z magazynu lokalnego wątku danych CRT bieżąca nazwa ustawień regionalnych. Informacje te są również dostępne za pomocą [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md) funkcji lub [setlocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md) funkcji.  
  
 Funkcje CRT wewnętrznej są specyficzne dla implementacji i może ulec zmianie z każdym wersję. Nie zaleca się ich użycie w kodzie.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`___lc_locale_name_func`|crt\src\setlocal.h|  
  
## <a name="see-also"></a>Zobacz też  
 [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md)   
 [setLocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../c-runtime-library/reference/free-locale.md)