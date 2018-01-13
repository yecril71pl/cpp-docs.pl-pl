---
title: "_get_fmode — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_fmode
- _get_fmode
dev_langs: C++
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50e3ebc4e1babed323200c720722648907b42c5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="getfmode"></a>_get_fmode
Pobiera domyślny tryb tłumaczenia pliku dla operacji We/Wy na plikach.  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _get_fmode(   
   int * pmode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pmode`  
 Wskaźnik do wartości całkowitej, należy podać bieżący tryb domyślny: `_O_TEXT` lub `_O_BINARY`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość zero w przypadku powodzenia; błąd o kodzie błędu. Jeśli `pmode` jest `NULL`, zgodnie z opisem w wywołaniu program obsługi nieprawidłowych parametrów [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja pobiera wartość [_fmode —](../../c-runtime-library/fmode.md) zmiennej globalnej. Ta zmienna Określa domyślny tryb tłumaczenia pliku dla obu niskiego poziomu i strumienia operacji We/Wy plików, takich jak `_open`, `_pipe`, `fopen`, i `freopen`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_get_fmode`|\<stdlib.h >|\<fcntl.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zapoznaj się z przykładem w [_set_fmode —](../../c-runtime-library/reference/set-fmode.md).  
  
## <a name="see-also"></a>Zobacz też  
 [_fmode —](../../c-runtime-library/fmode.md)   
 [_set_fmode —](../../c-runtime-library/reference/set-fmode.md)   
 [_setmode —](../../c-runtime-library/reference/setmode.md)   
 [We/Wy pliku w trybie binarnym i tekstowym](../../c-runtime-library/text-and-binary-mode-file-i-o.md)