---
title: fetestexcept1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: fetestexcept
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
- fetestexcept
- fenv/fetestexcept
dev_langs: C++
helpviewer_keywords: fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 78eb884950e2175815caf2ac645dc0e70c262566
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fetestexcept"></a>fetestexcept
Określa, które flagi stanu określony wyjątek zmiennoprzecinkowy, którego obecnie są ustawione.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fetestexcept(  
   int excepts  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `excepts`  
 Bitowe lub flagi stanu zmiennoprzecinkowe do testowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia zwraca maski bitowej zawierającego bitowe lub makra zmiennoprzecinkowych wyjątków, które odpowiadają flagi stanu wyjątek aktualnie ustawiona. Zwraca wartość 0, jeśli żadna z wyjątki są ustawione.  
  
## <a name="remarks"></a>Uwagi  
 Użyj funkcji fetestexcept, aby określić wyjątki, które zostały zgłoszone przez zmiennoprzecinkową punktu operacji. Użyj `excepts` parametr, aby określić flagi stanu wyjątek testu. `fetestexcept` Funkcja używa tych makr wyjątków zdefiniowane w \<fenv.h > w `excepts` i zwracana wartość:  
  
|Makra wyjątków|Opis|  
|---------------------|-----------------|  
|FE_DIVBYZERO|Wystąpił błąd singularity lub pole w wcześniej operacji zmiennoprzecinkowej; Utworzono wartości nieskończonej.|  
|FE_INEXACT|Funkcja wymuszono zaokrąglona wyniku przechowywanego wcześniej operacji zmiennoprzecinkowej.|  
|FE_INVALID|Wystąpił błąd domeny w wcześniej operacji zmiennoprzecinkowej.|  
|FE_OVERFLOW|Wystąpił błąd zakresu; wcześniej wynik operacji zmiennoprzecinkowej jest zbyt duży, może być reprezentowana.|  
|FE_UNDERFLOW|Wynik operacji zmiennoprzecinkowej wcześniej był za mały na pełne precyzji; wartość została utworzona.|  
|FE_ALLEXCEPT|Bitowe lub wszystkie obsługiwane wyjątki zmiennoprzecinkowe.|  
  
 Określony `excepts` argument może mieć wartość 0, jednej z makr wyjątków dotyczących liczb zmiennoprzecinkowych obsługiwanych lub operatora testu koniunkcji lub dwóch lub więcej makr. Efekt wszelkich innych `excepts` wartość argumentu jest niezdefiniowany.  
  
 Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`fetestexcept`|\<fenv.h >|\<cfenv >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feraiseexcept](../../c-runtime-library/reference/feraiseexcept.md)