---
title: ___lc_codepage_func | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: ___lc_codepage_func
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
dev_langs: C++
helpviewer_keywords: ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8532984c8557b095753c0e8cf30b6e63d8b01ce0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lccodepagefunc"></a>___lc_codepage_func
Funkcji CRT wewnętrznej. Pobiera bieżącej stronie kodowej wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
UINT ___lc_codepage_func(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Strona kodowa bieżącego wątku.  
  
## <a name="remarks"></a>Uwagi  
 `___lc_codepage_func`jest wewnętrzny funkcji CRT, która jest używana przez inne funkcje CRT można uzyskać z magazynu lokalnego wątku CRT danych bieżącej stronie kodowej. Informacje te są również dostępne za pomocą [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md) funkcji.  
  
 A *strona kodowa* mapowanie kody znaki jednobajtowe lub znaków dwubajtowych. Inny kod strony zawierają różne znaków specjalnych, zwykle dostosowywane do języka lub grupy języków. Aby uzyskać więcej informacji na temat stron kodowych, zobacz [stron kodowych](../c-runtime-library/code-pages.md).  
  
 Funkcje CRT wewnętrznej są specyficzne dla implementacji i może ulec zmianie z każdym wersję. Nie zaleca się ich użycie w kodzie.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`___lc_codepage_func`|crt\src\setlocal.h|  
  
## <a name="see-also"></a>Zobacz też  
 [_get_current_locale —](../c-runtime-library/reference/get-current-locale.md)   
 [setLocale, _wsetlocale —](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../c-runtime-library/reference/free-locale.md)