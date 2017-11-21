---
title: fegetexceptflag2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: fegetexceptflag
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetexceptflag
- fenv/fegetexceptflag
dev_langs: C++
helpviewer_keywords: fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0211ab1ec1e3144a0f9596b4500029b3f83095ee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fegetexceptflag"></a>fegetexceptflag
Zapisuje bieżący stan flagi określony wyjątek zmiennoprzecinkowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fegetexceptflag(   
   fexcept_t* pstatus,   
   int excepts   
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstatus`  
 Wskaźnik do `fexcept_t` obiektu zawiera bieżące wartości flag wyjątek określonych przez `excepts`.  
  
 `excepts`  
 Flagi wyjątek zmiennoprzecinkowy, którego mają być przechowywane w `pstatus`.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia zwraca wartość 0. W przeciwnym razie zwraca wartość inną niż zero.  
  
## <a name="remarks"></a>Uwagi  
 `fegetexceptflag` Funkcja przechowuje bieżący stan flagi stanu zmiennoprzecinkowych wyjątków, określony przez `excepts` w `fexcept_t` obiekt wskazywany przez `pstatus`.  `pstatus`musi wskazywać prawidłowe `fexcept_t` obiektu lub kolejnych zachowanie jest niezdefiniowana. `fegetexceptflag` Funkcja obsługuje makrach wyjątków zdefiniowane w \<fenv.h >:  
  
|Makra wyjątków|Opis|  
|---------------------|-----------------|  
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w wcześniej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|  
|FE_INEXACT|Funkcja wymuszono zaokrąglona wyniku przechowywanego wcześniej operacji zmiennoprzecinkowej.|  
|FE_INVALID|Wystąpił błąd domeny w wcześniej operacji zmiennoprzecinkowej.|  
|FE_OVERFLOW|Wystąpił błąd zakresu; wcześniej wynik operacji zmiennoprzecinkowej jest zbyt duży, może być reprezentowana.|  
|FE_UNDERFLOW|Wynik operacji zmiennoprzecinkowej wcześniej był za mały na pełne precyzji; wartość została utworzona.|  
|FE_ALLEXCEPT|Bitowe lub wszystkie obsługiwane wyjątki zmiennoprzecinkowe.|  
  
 `excepts` Argument może być równy zero, jednym z makr wyjątków dotyczących liczb zmiennoprzecinkowych obsługiwanych lub operatora testu koniunkcji lub dwóch lub więcej makr. Efekt dowolna inna wartość argumentu jest niezdefiniowany.  
  
 Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`fegetexceptflag`|\<fenv.h >|\<cfenv >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)