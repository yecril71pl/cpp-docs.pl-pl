---
title: fegetenv1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: fetegenv
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
- fegetenv
- fenv/fegetenv
dev_langs: C++
helpviewer_keywords: fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3da1a5837a2c2e3a2cd1c7987363b251bc67b567
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fegetenv"></a>fegetenv
Przechowuje bieżącego środowiska zmiennoprzecinkowe określonego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fegetenv(  
   fenv_t *penv  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `penv`  
 Wskaźnik do `fenv_t` obiektu zawiera bieżące wartości zmiennoprzecinkowych środowiska.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 0, jeśli środowisko zmiennoprzecinkowe pomyślnie była przechowywana w `penv`. W przeciwnym razie zwraca wartość inną niż zero.  
  
## <a name="remarks"></a>Uwagi  
 `fegetenv` Funkcja przechowuje bieżącego środowiska liczb zmiennoprzecinkowych w obiekcie wskazywana przez `penv`. Wartość zmiennoprzecinkowa punktu środowiska to zbiór flagi stanu i tryby kontroli, które mają wpływ na obliczenia liczb zmiennoprzecinkowych. W tym trybu zaokrąglania kierunku i flagi stanu zmiennoprzecinkowych wyjątków.  Jeśli `penv` nie wskazuje na prawidłową `fenv_t` obiekt, kolejne zachowanie jest niezdefiniowany.  
  
 Aby użyć tej funkcji, należy wyłączyć funkcję zmiennoprzecinkowe funkcje optymalizacji, które może uniemożliwić dostęp przy użyciu `#pragma fenv_access(on)` dyrektywy przed wywołaniem. Aby uzyskać więcej informacji, zobacz [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Nagłówek C|Nagłówek C++|  
|--------------|--------------|------------------|  
|`fegetenv`|\<fenv.h >|\<cfenv >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetenv](../../c-runtime-library/reference/fesetenv1.md)