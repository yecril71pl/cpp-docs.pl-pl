---
title: catanh catanhf, catanhl | Dokumentacja firmy Microsoft
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
- catanh
- catanhf
- catanhl
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
- catanh
- catanhf
- catanhl
- complex/catanh
- complex/catanhf
- complex/catanhl
dev_langs: C++
helpviewer_keywords:
- catanh function
- catanhf function
- catanhl function
ms.assetid: 1b6021cb-647a-41b4-9d7f-919cc8b57b86
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e9d04d9def767e9d674cde5b8e14c5be4fd9dcf5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="catanh-catanhf-catanhl"></a>catanh catanhf, catanhl
Pobiera odwrotny tangens hiperboliczny liczby złożone z części gałąź poza przedział [-1; + 1] na rzeczywistych osi.  
  
## <a name="syntax"></a>Składnia  
  
```  
_Dcomplex catanh(   
   _Dcomplex z   
);  
_Fcomplex catanh(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex catanh(   
   _Lcomplex z   
);  //  C++ only  
_Fcomplex catanhf(   
   _Fcomplex z   
);  
_Lcomplex catanhl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `z`  
 Liczba złożonych, która reprezentuje kąt w radianach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwrotny tangens hiperboliczny liczby `z`, w radianach. Wynik jest niepowiązany rzeczywistych osi, a w interwale [-iπ/2; + iπ/2] urojony osi. Błąd domeny wystąpi, jeśli `z` znajduje się poza interwał [-1, + 1]. Błąd bieguna wystąpi, jeśli `z` jest wartość -1 lub + 1.  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `catanh` który przyjmować i zwracać `_Fcomplex` i `_Lcomplex` wartości. W programie C `catanh` zawsze przyjmuje i zwraca `_Dcomplex` wartość.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Nagłówek C|Nagłówek C++|  
|-------------|--------------|------------------|  
|`catanh`,               `catanhf`, `catanhl`|\<COMPLEX.h >|\<ccomplex >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [ctanh ctanhf, ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan catanf, catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh csinhf, csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh casinhf, casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh ccoshf, ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh cacoshf, cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos cacosf, cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan ctanf, ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin csinf, csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin casinf, casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos ccosf, ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt csqrtf, csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)