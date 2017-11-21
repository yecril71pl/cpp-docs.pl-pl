---
title: cpow cpowf, cpowl | Dokumentacja firmy Microsoft
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
- cpow
- cpowf
- cpowl
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
- cpow
- cpowf
- cpowl
- complex/cpow
- complex/cpowf
- complex/copwl
dev_langs: C++
helpviewer_keywords:
- cpow function
- cpowf function
- complex/cpowl function
ms.assetid: 83fe2187-22b7-4295-ab16-4d77abdbb80b
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b8888a929380e150ad9f66e2e75caf48ccf89d21
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cpow-cpowf-cpowl"></a>cpow cpowf, cpowl
Pobiera wartość liczbę podniesioną do wskazanej potęgi, gdzie podstawowe i wykładnik są liczby złożone. Ta funkcja ma gałęzi Wytnij dla wykładnik rzeczywistych osi ujemna.  
  
## <a name="syntax"></a>Składnia  
  
```  
_Dcomplex cpow(   
   _Dcomplex x, _Dcomplex y   
);  
_Fcomplex cpow(   
   _Fcomplex x, _Fcomplex y   
);  // C++ only  
_Lcomplex cpow(   
   _Lcomplex x, _Lcomplex y   
);  // C++ only  
_Fcomplex cpowf(   
   _Fcomplex x, _Fcomplex y   
);  
_Lcomplex cpowl(   
   _Lcomplex x, _Lcomplex y   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Podstawa.  
  
 `y`  
 Wykładnik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość `x` podniesionej do potęgi równej `y` oddział Wytnij dla `x` rzeczywistych osi ujemna.  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `cpow` który przyjmować i zwracać `_Fcomplex` i `_Lcomplex` wartości. W programie C `cpow` zawsze przyjmuje i zwraca `_Dcomplex` wartość.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Nagłówek C|Nagłówek C++|  
|-------------|--------------|------------------|  
|`cpow`,               `cpowf`, `cpowl`|\<COMPLEX.h >|\<ccomplex >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp cexpf, cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [clog10 clog10f, clog10l](../../c-runtime-library/reference/clog10-clog10f-clog10l.md)   
 [clog, clogf, clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)