---
title: "_set_controlfp — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _set_controlfp
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
- set_controlfp
- _set_controlfp
dev_langs:
- C++
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b095fe13e8ecf20769ab833ace574d740fd185b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="setcontrolfp"></a>_set_controlfp
Ustawia słowa formantu zmiennoprzecinkowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __cdecl _set_controlfp(  
    unsigned int newControl,  
    unsigned int mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `newControl`  
 Nowe wartości bitowe słowa formantu.  
  
 `mask`  
 Maska nowe bity słowa formantu można ustawić.  
  
## <a name="return-value"></a>Wartość zwracana  
 Brak.  
  
## <a name="remarks"></a>Uwagi  
 `_set_controlfp` Jest podobny do `_control87`, ale określa tylko słowa formantu zmiennoprzecinkowe `newControl`. Bity w wartości wskazują stan formantu zmiennoprzecinkowych. Stan kontrolki zmiennoprzecinkowe pozwala programowi na zmienić dokładność, zaokrąglania i tryby infinity w pakiecie zmiennoprzecinkowej matematyczny. Możesz też zamaskować i anulować maskowanie wyjątki zmiennoprzecinkowe przy użyciu `_set_controlfp`. Aby uzyskać więcej informacji, zobacz [_control87 —, _controlfp —, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md).  
  
 Ta funkcja jest przestarzała podczas kompilowania za pomocą [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) ponieważ środowisko uruchomieniowe języka wspólnego obsługuje tylko domyślna dokładność zmiennoprzecinkowych.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Zgodność|  
|-------------|---------------------|-------------------|  
|`_set_controlfp`|\<float.h>|x86 tylko procesora|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)   
 [_clear87 —, _clearfp —](../../c-runtime-library/reference/clear87-clearfp.md)   
 [_status87, _statusfp, _statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)