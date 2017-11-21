---
title: csinh csinhf, csinhl | Dokumentacja firmy Microsoft
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
- csinh
- csinhf
- csinhl
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
- csinh
- csinhf
- csinhl
- complex/csinh
- complex/csinhf
- complex/csinhl
dev_langs: C++
helpviewer_keywords:
- csinh function
- csinhf function
- csinhl function
ms.assetid: cc616e55-d14d-4cd3-91f0-fbee03ce5edf
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65c3a74ecfbdfba27d0b1ac4dff37915e8b4c3a3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csinh-csinhf-csinhl"></a>csinh csinhf, csinhl
Pobiera sinus hiperboliczny liczby złożonej.  
  
## <a name="syntax"></a>Składnia  
  
```  
_Dcomplex csinh(   
   _Dcomplex z   
);  
_Fcomplex csinh(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex csinh(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex csinhf(   
   _Fcomplex z   
);  
_Lcomplex csinhl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `z`  
 Liczba złożonych, która reprezentuje kąt w radianach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Sinus hiperboliczny `z`, w radianach.  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `csinh` który przyjmować i zwracać `_Fcomplex` i `_Lcomplex` wartości. W programie C `csinh` zawsze przyjmuje i zwraca `_Dcomplex` wartość.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Nagłówek C|Nagłówek C++|  
|-------------|--------------|------------------|  
|`csinh`,               `csinhf`, `csinhl`|\<COMPLEX.h >|\<ccomplex >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh catanhf, catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh ctanhf, ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan catanf, catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [casinh casinhf, casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh ccoshf, ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh cacoshf, cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos cacosf, cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan ctanf, ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin csinf, csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin casinf, casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos ccosf, ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt csqrtf, csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)