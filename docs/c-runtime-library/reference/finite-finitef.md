---
title: "_finite —, _finitef | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _finite
- _finitef
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- finite
- _finite
- _finitef
- math/_finite
- math/_finitef
- float/_finite
dev_langs: C++
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb08c6a525222e8c1bb886f87aa55b2996cd3846
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="finite-finitef"></a>_finite —, _finitef
Określa, czy wartość zmiennoprzecinkowa jest jednak ograniczona.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _finite(   
   double x   
);  
  
int _finitef(   
   float x   
); /* x64 and ARM/ARM64 only */  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa do testowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zarówno `_finite` i `_finitef` zwrócić wartość niezerową, jeśli argument *x* jest nieskończona; będący, jeśli -INF < `x` < + INF. Zwraca 0, jeśli argument ma nieograniczony lub NAN.  
  
## <a name="remarks"></a>Uwagi  
 `_finite` i `_finitef` funkcje są określone firmy Microsoft. `_finitef` Funkcja tylko jest dostępna, gdy skompilowanego dla x86, ARM i ARM64 platform.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|  
|--------------|---------------------------|-------------------------------|  
|`_finite`|\<float.h — > lub \<math.h >|\<float.h — >, \<math.h >, \<cfloat — >, lub \<cmath >|  
|`_finitef`|\<Math.h >|\<Math.h > lub \<cmath >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [isNaN _isnan —, _isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [_fpclass, _fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)