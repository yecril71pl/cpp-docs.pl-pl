---
title: cimag, cimagf, cimagl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- cimag
- cimagf
- cimagl
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
- cimagf
- cimagl
- complex/cimag
- complex/cimagf
- complex/cimagl
- cimag
dev_langs:
- C++
helpviewer_keywords:
- cimag function
- cimagf function
- cimagl function
ms.assetid: 0d8836f5-d61d-44cd-8731-6f75cb776def
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9802a682193a0ef805f4a6964bf0aa1682a7619b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="cimag-cimagf-cimagl"></a>cimag, cimagf, cimagl
Pobiera wyrażenie Liczba_zespolona część liczbą.  
  
## <a name="syntax"></a>Składnia  
  
```  
double cimag(   
   _Dcomplex z   
);  
float cimag(   
   _Fcomplex z   
);  // C++  
long double cimag(   
  _Lcomplex z   
);  // C++  
float cimagf(   
   _Fcomplex z   
);  
long double cimagl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `z`  
 Liczba złożonych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wyrażenie Liczba_zespolona część `z`.  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `cimag` które trwają `_Fcomplex` lub `_Lcomplex` wartości i wróć `float` lub `long double` wartości. W programie C `cimag` zawsze ma `_Dcomplex` wartości i zwraca `double` wartość.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Nagłówek C|Nagłówek C++|  
|-------------|--------------|------------------|  
|`cimag`,               `cimagf`, `cimagl`|\<complex.h>|\<ccomplex >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [normy normf, norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal crealf, creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj, cprojf, cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [conj, conjf, conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [carg cargf, cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [cabs, cabsf, cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)