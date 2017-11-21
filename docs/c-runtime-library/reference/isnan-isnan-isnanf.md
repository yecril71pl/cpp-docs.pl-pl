---
title: "isNaN _isnan —, _isnanf | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
dev_langs: C++
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 982760deff4c5e2439c8743aa0de736a24faa02a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="isnan-isnan-isnanf"></a>isNaN _isnan —, _isnanf
Testy, jeśli wartość zmiennoprzecinkowa nie jest liczbą (NAN).  
  
## <a name="syntax"></a>Składnia  
  
```  
int isnan(  
   /* floating-point */ x   
); /* C-only macro */  
  
int _isnan(  
   double x   
);  
  
int _isnanf(  
   float x  
); /* x64 only */  
  
template <class T>  
bool isnan(  
   T x  
) throw(); /* C++ only */  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 Wartość zmiennoprzecinkowa do testowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 W języku C `isnan` makro i `_isnan` i `_isnanf` funkcje zwracają wartość niezerową, jeśli argument `x` jest wartością typu NAN; w przeciwnym razie zwracają 0.  
  
 W języku C++ `isnan` szablonu funkcje zwracają `true` Jeśli argument `x` jest wartością typu NAN; w przeciwnym razie zwraca `false`.  
  
## <a name="remarks"></a>Uwagi  
 C `isnan` makro i `_isnan` i `_isnanf` funkcji testowania wartość zmiennoprzecinkowa *x*, zwracając wartość niezerową, jeśli *x* nie jest wartość liczbą (NAN). NAN jest generowany, gdy wynik operacji zmiennoprzecinkowej nie może być reprezentowany w formacie zmiennoprzecinkowej IEEE-754 dla określonego typu. Informacje, jak NAN są reprezentowane dla danych wyjściowych, zobacz [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
 Podczas kompilacji jako C++, `isnan` makro nie jest zdefiniowany i `isnan` funkcji szablonu jest zdefiniowany w zamian. Zwraca wartość typu `bool` zamiast liczbą całkowitą.  
  
 `_isnan` i `_isnanf` funkcje są określone firmy Microsoft. `_isnanf` Funkcja jest dostępna, gdy kompilowany dla x64 tylko.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|  
|-------------|---------------------------|-------------------------------|  
|`isnan`, `_isnanf`|\<Math.h >|\<Math.h > lub \<cmath >|  
|`_isnan`|\<float.h — >|\<float.h — > lub \<cfloat — >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [_finite —, _finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [_fpclass, _fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)