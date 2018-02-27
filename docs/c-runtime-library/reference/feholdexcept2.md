---
title: feholdexcept2 | Dokumentacja firmy Microsoft
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
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
dev_langs:
- C++
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbfef5db5871740744e370d7e1ac86cf7abac8ac
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="feholdexcept"></a>feholdexcept
Zapisuje bieżące środowisko liczb zmiennoprzecinkowych w określonym obiekcie czyści flagi stanu zmiennoprzecinkowych i, jeśli to możliwe, umieszcza liczb zmiennoprzecinkowych środowiska do zatrzymania z systemem innym niż tryb.  
  
## <a name="syntax"></a>Składnia  
  
```  
int feholdexcept(  
   fenv_t *penv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `penv`  
 Wskaźnik do `fenv_t` obiekt zawierający kopię zmiennoprzecinkowe środowiska.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca zero tylko wtedy, gdy funkcja jest w stanie pomyślnie włączyć-stop zmiennoprzecinkowych wyjątków.  
  
## <a name="remarks"></a>Uwagi  
 `feholdexcept` Funkcja służy do przechowywania stanu bieżącego środowiska ruchomy punkt w `fenv_t` obiekt wskazywany przez `penv`i można ustawić środowiska, aby nie przerywać wykonywanie na wyjątki zmiennoprzecinkowe. Jest to nazywane tryb bez zatrzymania.  Ten tryb jest kontynuowany do momentu przywrócenia środowiska przy użyciu [fesetenv](fesetenv1.md) lub [feupdateenv](../../c-runtime-library/reference/feupdateenv.md).  
  
 Funkcja ta jest przydatna na początku procedury wymagające Ukryj co najmniej jeden wyjątki zmiennoprzecinkowe wywołujący. Aby zgłosić wyjątek, może po prostu wyczyścić niechciane wyjątków przy użyciu [feclearexcept,](../../c-runtime-library/reference/feclearexcept1.md) , a następnie zakończyć tryb-stop wywołaniem `feupdateenv`.  
  
 Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`feholdexcept`|\<fenv.h>|\<cfenv>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [fesetenv](fesetenv1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)