---
title: fesetexceptflag2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
dev_langs:
- C++
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24aff3007d88f9ae5ebc30811e652284ecebeba5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="fesetexceptflag"></a>fesetexceptflag
Ustawia flagi określony stan liczb zmiennoprzecinkowych w bieżącym środowisku zmiennoprzecinkowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fesetexceptflag(  
     const fexcept_t *pstatus,  
     int excepts  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstatus`  
 Wskaźnik do `fexcept_t` obiekt zawierający wartości, które mają ustawioną wartość wyjątek flagi stanu. Obiekt może zostać ustawiona przez poprzednie wywołanie [fegetexceptflag](fegetexceptflag2.md).  
  
 `excepts`  
 Flagi stanu wyjątek zmiennoprzecinkowy, którego można ustawić.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 0, jeśli pomyślnie ustawiono wszystkie flagi stanu określonego wyjątku. W przeciwnym razie zwraca wartość różną od zera.  
  
## <a name="remarks"></a>Uwagi  
 `fesetexceptflag` Funkcja ustawia stan flagi stanu zmiennoprzecinkowych wyjątków, określony przez `excepts` do odpowiedniej wartości `fexcept_t` obiekt wskazywany przez `pstatus`.  Zgłaszaj wyjątków. `pstatus` Wskaźnika musi wskazywać prawidłowe `fexcept_t` obiektu lub kolejnych zachowanie jest niezdefiniowana. `fesetexceptflag` Funkcja obsługuje te wartości makra wyjątków w `excepts`zdefiniowanej w \<fenv.h >:  
  
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
|`fesetexceptflag`|\<fenv.h>|\<cfenv>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetexceptflag](../../c-runtime-library/reference/fegetexceptflag2.md)