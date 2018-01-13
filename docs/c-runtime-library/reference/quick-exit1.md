---
title: quick_exit1 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: quick_exit
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
- quick_exit
- process/quick_exit
- stdlib/quick_exit
dev_langs: C++
helpviewer_keywords: quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fb6a8bdea6cb37bd70d6aeda490e2470aa74e999
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="quickexit"></a>quick_exit
Powoduje, że Kończenie działania programu normalne występuje.  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec(noreturn) void quick_exit(  
    int status  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 stan  
 Kod stanu, aby powrócić do środowiska hosta.  
  
## <a name="return-value"></a>Wartość zwracana  
 `quick_exit` Funkcji nie można wrócić do swojego obiektu wywołującego.  
  
## <a name="remarks"></a>Uwagi  
 `quick_exit` Funkcja powoduje zakończenie normalne programu. Wywołuje żadnych funkcji w zarejestrowany przez `atexit`, `_onexit` lub sygnału zarejestrowany przez programy obsługi `signal` funkcji. Zachowanie jest niezdefiniowana, jeśli `quick_exit` jest wywoływana więcej niż po lub jeśli `exit` funkcja jest również nazywany.  
  
 `quick_exit` Funkcji wywołań w ostatniej w kolejności wytworzenia, funkcje zarejestrowane przez `at_quick_exit`, z wyjątkiem tych funkcji już wywoływane, gdy funkcja została zarejestrowana.  Zachowanie jest niezdefiniowana, jeśli [longjmp](../../c-runtime-library/reference/longjmp.md) wywołanie podczas wywoływania zarejestrowanej funkcji, który może obsłużyć wywołania funkcji.  
  
 Po wywołaniu funkcji zarejestrowanych `quick_exit` wywołuje `_Exit` przy użyciu `status` wartość zwracana kontroli w środowisku hosta.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`quick_exit`|\<process.h > lub \<stdlib.h >|  
  
 Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [przerwania](../../c-runtime-library/reference/abort.md)   
 [atexit —](../../c-runtime-library/reference/atexit.md)   
 [_execwexec — funkcje](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _exit — _exit —](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit —, _onexit_m —](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn, _wspawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)