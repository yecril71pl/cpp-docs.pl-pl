---
title: __pctype_func | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __pctype_func
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords: __pctype_func
dev_langs: C++
helpviewer_keywords: __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae2c5f53c10083deb281a88a5f398712722700b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="pctypefunc"></a>__pctype_func
Pobiera wskaźnik do tablicy znaków informacji o klasyfikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
const unsigned short *__pctype_func(  
   )  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do tablicy znaków informacji o klasyfikacji.  
  
## <a name="remarks"></a>Uwagi  
 Informacje w tabeli klasyfikacji znaków jest tylko do użytku wewnętrznego i jest używana przez różne funkcje, które klasyfikowania znaków typu `char`. Aby uzyskać więcej informacji, zobacz `Remarks` sekcji [_pctype —, _pwctype —, _wctype —, _mbctype —, _mbcasemap —](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|__pctype_func|CType.h|  
  
## <a name="see-also"></a>Zobacz też  
 [_pctype — _pwctype —, _wctype —, _mbctype —, _mbcasemap —](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)