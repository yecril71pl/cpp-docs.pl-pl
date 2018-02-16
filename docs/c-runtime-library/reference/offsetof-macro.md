---
title: offsetof Macro | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
- offsetof
dev_langs:
- C++
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a70bb2823f29caf3f76224bfb91c3c9642bbdcf1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="offsetof-macro"></a>offsetof Macro
Pobiera przesunięcie elementu członkowskiego z początku jego struktury nadrzędnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      size_t offsetof(  
   structName,  
   memberName   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *structName*  
 Nazwa nadrzędnego struktury danych.  
  
 `memberName`  
 Nazwa elementu członkowskiego w nadrzędnej struktury danych do ustalania przesunięcie.  
  
## <a name="return-value"></a>Wartość zwracana  
 `offsetof` Zwraca przesunięcie w bajtach określonego elementu członkowskiego, od początku jej nadrzędnej struktury danych. Jest niezdefiniowany dla pól bitowych.  
  
## <a name="remarks"></a>Uwagi  
 `offsetof` Makro zwraca przesunięcie w bajtach `memberName` od początku struktury określony przez *structName* jako wartość typu `size_t`. Można określić typy z `struct` — słowo kluczowe.  
  
> [!NOTE]
>  `offsetof` nie jest funkcją i nie może być opisana przy użyciu prototypu C.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`offsetof`|\<stddef.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)