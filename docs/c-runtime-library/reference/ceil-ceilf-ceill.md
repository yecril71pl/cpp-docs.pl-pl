---
title: "ceil ceilf —, ceill — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ceilf
- ceil
- ceill
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ceil
- ceilf
- ceill
dev_langs: C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4831b9f6f046dbc1a5d337f22e6be3dc3f4a5662
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ceil-ceilf-ceill"></a>ceil, ceilf, ceill
Oblicza Zaokrąglenie w górę wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
double ceil(   
   double x   
);  
float ceil(  
   float x  
);  // C++ only  
long double ceil(  
   long double x  
);  // C++ only  
float ceilf(  
   float x  
);  
long double ceill(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Wartość zmiennoprzecinkowa.  
  
## <a name="return-value"></a>Wartość zwracana  
 `ceil` Zwracają wartość zmiennoprzecinkowa, która reprezentuje najmniejsza liczba całkowita, która jest większa niż lub równa `x`. Nie ma żadnych zwracany błąd.  
  
|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|brak|`_DOMAIN`|  
  
 `ceil`zawiera implementację, która używa Streaming SIMD Extensions 2 (SSE2). Aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2, zobacz [_set_sse2_enable —](../../c-runtime-library/reference/set-sse2-enable.md).  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `ceil`. W programie C `ceil` zawsze przyjmuje i zwraca wartość o podwójnej precyzji.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`ceil`, `ceilf`, `ceill`|\<Math.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [floor](../../c-runtime-library/reference/floor-floorf-floorl.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [FLOOR floorf —, floorl —](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod —, fmodf —](../../c-runtime-library/reference/fmod-fmodf.md)   
 [round, roundf, roundl](../../c-runtime-library/reference/round-roundf-roundl.md)
