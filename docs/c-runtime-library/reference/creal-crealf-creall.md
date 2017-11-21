---
title: creal crealf, creall | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
dev_langs: C++
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 060ac8704fdb3d17e46452ff369368785a43bc8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creal-crealf-creall"></a>creal crealf, creall
Pobiera część rzeczywista liczbą.  
  
## <a name="syntax"></a>Składnia  
  
```  
double creal(   
   _Dcomplex z   
);  
float creal(   
   _Fcomplex z   
);  // C++ only  
long double creal(   
   _Lcomplex z   
);  // C++ only  
float crealf(   
   _Fcomplex z   
);  
long double creall(   
  _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `z`  
 Liczba złożonych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Część rzeczywista `z`.  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `creal` które trwają `_Fcomplex` lub `_Lcomplex` wartości i wróć `float` lub `long double` wartości. W programie C `creal` zawsze ma `_Dcomplex` wartości i zwraca `double` wartość.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Nagłówek C|Nagłówek C++|  
|-------------|--------------|------------------|  
|`creal`,               `crealf`, `creall`|\<COMPLEX.h >|\<ccomplex >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [normy normf, norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [cproj cprojf, cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [conj conjf, conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag cimagf, cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg cargf, cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [pliki cab, cabsf, cabsl —](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)