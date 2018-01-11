---
title: "_ftell_nolock —, _ftelli64_nolock — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ftelli64_nolock
- _ftell_nolock
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
- _ftelli64_nolock
- ftelli64_nolock
- ftell_nolock
- _ftell_nolock
dev_langs: C++
helpviewer_keywords:
- ftelli64_nolock function
- _ftelli64_nolock function
- _ftell_nolock function
- ftell_nolock function
- file pointers [C++], getting current position
ms.assetid: 84e68b0a-32f8-4c4a-90ad-3f2387685ede
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24d5ad81bb19f5a33eb70f6dc40ef41cc5d761d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ftellnolock-ftelli64nolock"></a>_ftell_nolock, _ftelli64_nolock
Pobiera bieżącą pozycję wskaźnika pliku, bez blokowania wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
long _ftell_nolock(   
   FILE *stream   
);  
__int64 _ftelli64_nolock(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Docelowy `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Taki sam jak `ftell` i `_ftelli64`. Aby uzyskać więcej informacji, zobacz [ftell —, _ftelli64 —](../../c-runtime-library/reference/ftell-ftelli64.md)**.**  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje są bez blokowania wersje `ftell` i `_ftelli64`odpowiednio. Są one takie same jak `ftell` i `_ftelli64` z tą różnicą, że nie są chronione przez inne wątki od zakłóceń. Funkcje te mogą być szybciej, ponieważ one nie nakładu zablokowania inne wątki. Ich używać tylko w kontekstach wątkowo, np. aplikacje jednowątkowe lub gdzie wywoływania zakres już obsługuje izolacji wątku.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|  
|--------------|---------------------|---------------------|  
|`ftell_nolock`|\<stdio.h >|\<errno.h >|  
|`_ftelli64_nolock`|\<stdio.h >|\<errno.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fgetpos —](../../c-runtime-library/reference/fgetpos.md)   
 [fseek, _fseeki64 —](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [_lseek —, _lseeki64 —](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [ftell, _ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)