---
title: "_endthread —, _endthreadex — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _endthread
- _endthreadex
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
- _endthread
- endthreadex
- _endthreadex
- endthread
dev_langs: C++
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5abe2f0aa2f62048fefb2f79614e018fbdb51e08
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="endthread-endthreadex"></a>_endthread, _endthreadex
Zakończenie wątku; `_endthread` zakończenie wątku, który jest tworzony przez `_beginthread` i `_endthreadex` zakończenie wątku, który jest tworzony przez `_beginthreadex`.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _endthread( void );  
void _endthreadex(   
   unsigned retval   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `retval`  
 Wątek kodu zakończenia.  
  
## <a name="remarks"></a>Uwagi  
 Możesz wywołać `_endthread` lub `_endthreadex` jawnie na zakończenie wątku; jednak `_endthread` lub `_endthreadex` automatycznie jest wywoływane, gdy wątek zwraca rutynowych przekazany jako parametr `_beginthread` lub `_beginthreadex`. Przerywanie wątków w wyniku wywołania `endthread` lub `_endthreadex` ułatwia odzyskiwanie odpowiednich zasobów przydzielonych dla wątku.  
  
> [!NOTE]
>  Dla pliku wykonywalnego połączone z Libcmt.lib, nie należy wywoływać Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) interfejsu API; zapobiega to system czasu wykonywania odzyskiwania przydzielone zasoby. `_endthread`i `_endthreadex` odzyskać wątku przydzielone zasoby, a następnie wywołać `ExitThread`.  
  
 `_endthread`dojście wątku jest automatycznie zamykany. (To zachowanie różni się od środowiska Win32 `ExitThread` interfejsu API.) W związku z tym, kiedy należy używać `_beginthread` i `_endthread`, nie zamykaj jawnie dojście wątku przez wywołanie Win32 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) interfejsu API.  
  
 Środowiska Win32, takich jak `ExitThread` interfejsu API, `_endthreadex` nie zamyka dojście wątku. W związku z tym, kiedy należy używać `_beginthreadex` i `_endthreadex`, należy zamknąć dojście wątku przez wywołanie Win32 `CloseHandle` interfejsu API.  
  
> [!NOTE]
>  `_endthread`i `_endthreadex` spowodować destruktory C++ do czasu w wątku nie ma zostać wywołana.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_endthread`|\<process.h >|  
|`_endthreadex`|\<process.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wielowątkowe wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_beginthread —](../../c-runtime-library/reference/beginthread-beginthreadex.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)