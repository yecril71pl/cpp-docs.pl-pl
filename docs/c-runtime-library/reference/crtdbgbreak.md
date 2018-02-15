---
title: _CrtDbgBreak | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtDbgBreak
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
apitype: DLLExport
f1_keywords:
- _CrtDbgBreak
- CrtDbgBreak
dev_langs:
- C++
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f49870ace2b23983d7eb121cd18ea3d755250e51
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="crtdbgbreak"></a>_CrtDbgBreak
Ustawia punkt przerwania na określonej linii kodu. (Używane tylko w trybie debugowania.)  
  
## <a name="syntax"></a>Składnia  
  
```  
void _CrtDbgBreak( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Nie mają żadnej wartości zwracanych.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtDbgBreak` Funkcja ustawia punkt przerwania debugowania na określonej linii kodu gdzie znajduje się funkcja. Ta funkcja jest używana tylko w trybie debugowania i jest zależna od `_DEBUG` został wcześniej określony.  
  
 Aby uzyskać więcej informacji na temat korzystania innych obsługą punktu zaczepienia funkcji środowiska wykonawczego i pisanie własnych klienta zdefiniowane przez funkcje punktów zaczepienia, zobacz [zapisywania swój własny debugowanie funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtDbgBreak`|\<CRTDBG.h>|  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [__debugbreak](../../intrinsics/debugbreak.md)