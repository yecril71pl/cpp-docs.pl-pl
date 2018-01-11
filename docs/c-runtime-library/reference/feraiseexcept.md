---
title: feraiseexcept | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: feraiseexcept
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
apitype: HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
dev_langs: C++
helpviewer_keywords: feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ab77da8cee422bab618dc8737ad254b65301ffd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="feraiseexcept"></a>feraiseexcept
Wywołuje określone wyjątki zmiennoprzecinkowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
int feraiseexcept(  
   int excepts  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `excepts`  
 Wyjątki zmiennoprzecinkowe, aby wywołać.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli wszystkie określone wyjątki pojawienia się pomyślnie, zwraca wartość 0.  
  
## <a name="remarks"></a>Uwagi  
 `feraiseexcept` Funkcja próbuje zgłaszać wyjątki zmiennoprzecinkowe określony przez `excepts`.   `feraiseexcept` Funkcja obsługuje makrach wyjątków zdefiniowane w \<fenv.h >:  
  
|Makra wyjątków|Opis|  
|---------------------|-----------------|  
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w wcześniej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|  
|FE_INEXACT|Funkcja wymuszono zaokrąglona wyniku przechowywanego wcześniej operacji zmiennoprzecinkowej.|  
|FE_INVALID|Wystąpił błąd domeny w wcześniej operacji zmiennoprzecinkowej.|  
|FE_OVERFLOW|Wystąpił błąd zakresu; wcześniej wynik operacji zmiennoprzecinkowej jest zbyt duży, może być reprezentowana.|  
|FE_UNDERFLOW|Wynik operacji zmiennoprzecinkowej wcześniej był za mały na pełne precyzji; wartość została utworzona.|  
|FE_ALLEXCEPT|Bitowe lub wszystkie obsługiwane wyjątki zmiennoprzecinkowe.|  
  
 `excepts` Argument może być równy zero, jednej z wartości makra wyjątków lub operatora testu koniunkcji lub dwóch lub więcej z makr wyjątków obsługiwanych. Po spełnieniu jednego z makr wyjątków określony FE_OVERFLOW lub FE_UNDERFLOW, może zostać zgłoszony wyjątek FE_INEXACT, jako efektem ubocznym.  
  
 Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).  
  
 **Microsoft Specific:** wyjątki określone w `excepts` są wywoływane w kolejności FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Jednak FE_INEXACT mogą być wywoływane, gdy FE_OVERFLOW lub FE_UNDERFLOW jest wywoływane, nawet jeśli nie zostanie określony w `excepts`. **Końcowy określonych firmy Microsoft**  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`feraiseexcept`|\<fenv.h >|\<cfenv >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)