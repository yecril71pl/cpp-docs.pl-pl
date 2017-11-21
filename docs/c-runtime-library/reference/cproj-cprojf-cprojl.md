---
title: cproj cprojf, cprojl | Dokumentacja firmy Microsoft
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
- cproj
- cprojf
- cprojl
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
- cproj
- cprojf
- cprojl
- complex/cproj
- complex/cprojf
- complex/cprojl
dev_langs: C++
helpviewer_keywords:
- cproj function
- cprojf function
- cprojl function
ms.assetid: 32b49623-13bf-4cae-802e-7912d75030fe
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a627a629bc095ecc01f7f7f3b866c05047205340
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cproj-cprojf-cprojl"></a>cproj cprojf, cprojl
Pobiera projekcji liczbą sfery Reimann.  
  
## <a name="syntax"></a>Składnia  
  
```  
_Dcomplex cproj(   
   _Dcomplex z   
);  
_Fcomplex cproj(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cproj(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cprojf(   
   _Fcomplex z   
);  
_Lcomplex cprojl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `z`  
 Liczba złożonych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Rzutowanie `z` sfery Reimann.  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `cproj` który przyjmować i zwracać `_Fcomplex` i `_Lcomplex` wartości. W programie C `cproj` zawsze przyjmuje i zwraca `_Dcomplex` wartość.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Nagłówek C|Nagłówek C++|  
|-------------|--------------|------------------|  
|`cproj`,               `cprojf`, `cprojl`|\<COMPLEX.h >|\<ccomplex >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [normy normf, norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal crealf, creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [conj conjf, conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag cimagf, cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg cargf, cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [pliki cab, cabsf, cabsl —](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)