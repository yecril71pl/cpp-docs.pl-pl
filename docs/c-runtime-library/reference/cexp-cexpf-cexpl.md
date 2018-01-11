---
title: cexp cexpf, cexpl | Dokumentacja firmy Microsoft
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
- cexp
- cexpf
- cexpl
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
- cexp
- cexpf
- cexpl
- complex/cepx
- complex/cexpf
- complex/cexpl
dev_langs: C++
helpviewer_keywords:
- cexp function
- cexpl function
- cexpf function
ms.assetid: f27fd5a9-70c7-4957-a7ee-5256d19bd1da
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f7138d3853faad1268148ef7517291a849525df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cexp-cexpf-cexpl"></a>cexp cexpf, cexpl
Obliczenia bazy danych base e wykładniczej z liczbą.  
  
## <a name="syntax"></a>Składnia  
  
```  
_Dcomplex cexp(   
   _Dcomplex z   
);  
_Fcomplex cexp(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex cexp(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex cexpf(   
  _Fcomplex z   
);  
_Lcomplex cexpl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `z`  
 Liczba złożonych, która reprezentuje wykładnik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość `e` podniesionej do potęgi równej `z`.  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia `cexp` który przyjmować i zwracać `_Fcomplex` i `_Lcomplex` wartości. W programie C `cexp` zawsze przyjmuje i zwraca `_Dcomplex` wartość.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Nagłówek C|Nagłówek C++|  
|-------------|--------------|------------------|  
|`cexp`,               `cexpf`, `cexpl`|\<COMPLEX.h >|\<COMPLEX.h >|  
  
 Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cpow cpowf, cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog10 clog10f, clog10l](../../c-runtime-library/reference/clog10-clog10f-clog10l.md)   
 [clog, clogf, clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)