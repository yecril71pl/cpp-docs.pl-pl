---
title: "_fseek_nolock —, _fseeki64_nolock — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fseek_nolock
- _fseeki64_nolock
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
apitype: DLLExport
f1_keywords:
- _fseek_nolock
- _fseeki64_nolock
- fseek_nolock
- fseeki64_nolock
dev_langs: C++
helpviewer_keywords:
- _fseek_nolock function
- fseeki64_nolock function
- file pointers [C++], moving
- fseek_nolock function
- _fseeki64_nolock function
- seek file pointers
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e113c9a1f805fea5d1b5a9a10052f89a2bfa43cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fseeknolock-fseeki64nolock"></a>_fseek_nolock, _fseeki64_nolock
Przenosi wskaźnika pliku do określonej lokalizacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _fseek_nolock(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64_nolock(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
 `offset`  
 Liczba bajtów z`origin.`  
  
 `origin`  
 Pozycja początkowa.  
  
## <a name="return-value"></a>Wartość zwracana  
 Taki sam jak [fseek, _fseeki64 —](../../c-runtime-library/reference/fseek-fseeki64.md) odpowiednio.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje są wersje — blokowanie `fseek` i `_fseeki64`odpowiednio. Są one takie same jak `fseek` i `_fseeki64` z tą różnicą, że nie są chronione przez inne wątki od zakłóceń. Funkcje te mogą być szybciej, ponieważ one nie nakładu zablokowania inne wątki. Ich używać tylko w kontekstach wątkowo, np. aplikacje jednowątkowe lub gdzie wywoływania zakres już obsługuje izolacji wątku.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fseek`|\<stdio.h >|  
|`_fseeki64`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [ftell —, _ftelli64 —](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [_lseek —, _lseeki64 —](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [rewind](../../c-runtime-library/reference/rewind.md)