---
title: "_findclose — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _findclose
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _findclose
- findclose
dev_langs: C++
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4747592dbda7a903d5d8a50cebde9ef006ec765d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="findclose"></a>_findclose
Zamyka dojście wyszukiwania i zwalnia zasoby skojarzone.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _findclose(   
   intptr_t handle   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `handle`  
 Dojście wyszukiwania zwrócony przez poprzednie wywołanie `_findfirst`.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `_findclose` zwraca wartość 0. W przeciwnym razie zwraca wartość -1 i ustawia `errno` do `ENOENT`, wskazujący, że już pasujących plików można znaleźć.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_findclose`|\<IO.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywołania systemowe](../../c-runtime-library/system-calls.md)   
 [Funkcje wyszukiwania nazwy pliku](../../c-runtime-library/filename-search-functions.md)