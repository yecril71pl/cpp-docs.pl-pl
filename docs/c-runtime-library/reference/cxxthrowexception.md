---
title: "_Cxxthrowexception — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CxxThrowException
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
- CxxThrowException
- _CxxThrowException
dev_langs:
- C++
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fb59e3e81a9e92d3a692e91c9c25a92fd09603cd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="cxxthrowexception"></a>_CxxThrowException
Tworzy rekord wyjątku i wywołuje środowiska uruchomieniowego zaczął przetwarzać wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
extern "C" void __stdcall _CxxThrowException(  
   void* pExceptionObject  
   _ThrowInfo* pThrowInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `pExceptionObject`  
 Obiekt, który wygenerował wyjątek.  
  
 [in] `pThrowInfo`  
 Informacje wymagane do przetwarzania wyjątek.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda znajduje się w pliku tylko do kompilatora kompilator używa do przetwarzania wyjątków. Nie wywołuj metody bezpośrednio w kodzie.  
  
## <a name="requirements"></a>Wymagania  
 **Źródło:** Throw.cpp  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne zestawienie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)