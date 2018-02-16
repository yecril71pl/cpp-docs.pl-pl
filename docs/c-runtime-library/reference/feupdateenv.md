---
title: feupdateenv | Dokumentacja firmy Microsoft
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
- feupdateenv
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
- feupdateenv
- fenv/feupdateenv
dev_langs:
- C++
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd4a74515b2b3ab29b30fb07d80121e35d950ee
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="feupdateenv"></a>feupdateenv
Zapisuje obecnie zgłoszono wyjątki zmiennoprzecinkowe, przywraca stan określonego środowiska liczb zmiennoprzecinkowych, a następnie wywołuje zapisane wyjątki zmiennoprzecinkowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
int feupdateenv(  
   const fenv_t* penv  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `penv`  
 Wskaźnik do `fenv_t` obiekt, który zawiera zmiennoprzecinkowe środowiska zgodnie z ustaleniami przez wywołanie do [fegetenv](fegetenv1.md) lub [feholdexcept](feholdexcept2.md). Można również określić domyślnego środowiska zmiennoprzecinkowe uruchamiania za pomocą makra FE_DFL_ENV.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 0, jeśli wszystkie działania ukończone pomyślnie. W przeciwnym razie zwraca wartość różną od zera.  
  
## <a name="remarks"></a>Uwagi  
 `feupdateenv` Funkcja wykonuje wiele operacji. Po pierwsze przechowuje bieżące flagi stanu zgłoszono wyjątek zmiennoprzecinkowy, którego w magazynie automatycznego. Następnie, ustawia bieżącego środowiska zmiennoprzecinkowe z wartości przechowywanej w `fenv_t` obiekt wskazywany przez `penv`. Jeśli `penv` nie jest FE_DFL_ENV lub nie wskazuje na prawidłową `fenv_t` obiekt, kolejne zachowanie jest niezdefiniowany. Na koniec `feupdateenv` zgłasza wyjątki zmiennoprzecinkowe przechowywane lokalnie.  
  
 Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`feupdateenv`|\<fenv.h>|\<cfenv>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)