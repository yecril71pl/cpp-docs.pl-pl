---
title: setjmp | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- setjmp
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
- setjmp
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ef5c4b0e026090718fc02dd109a1fccb91152010
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="setjmp"></a>setjmp
Zapisuje bieżący stan programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int setjmp(  
   jmp_buf env   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `env`  
 Zmienna, w której jest przechowywany środowiska.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 0 po zapisaniu środowiska stosu. Jeśli `setjmp` zwraca w `longjmp` wywołać, zwraca `value` argument `longjmp`, lub jeśli `value` argument `longjmp` ma wartość 0, `setjmp` zwraca wartość 1. Nie ma żadnych zwracany błąd.  
  
## <a name="remarks"></a>Uwagi  
 `setjmp` Funkcja zapisuje środowisku stosu, którego będzie można później przywrócić, przy użyciu `longjmp`. Podczas łączenia `setjmp` i `longjmp` umożliwiają wykonanie innego niż lokalne `goto`. One są zwykle używane do przekazania Kontrola wykonywania kodu służącego do obsługi błędów lub odzyskiwania w wcześniej wywołana procedura bez użycia normalne wywołanie lub return Konwencji.  
  
 Wywołanie `setjmp` jest zapisywany w bieżącym środowisku stosu w `env`. Kolejne wywołania `longjmp` przywraca zapisanego środowiska i zwraca sterowania do punktu zaraz po odpowiadającego `setjmp` wywołania. Wszystkie zmienne (z wyjątkiem zmiennych rejestru) dostępny do procedury odbieranie kontroli zawierają wartości podczas obliczania miało `longjmp` została wywołana.  
  
 Nie jest możliwe użycie `setjmp` na przejście z kodu natywnego do zarządzanego kodu.  
  
 **Uwaga** `setjmp` i `longjmp` nie obsługują semantyki obiektu języka C++. W programach języka C++ użyj mechanizmu obsługi wyjątków C++.  
  
 Aby uzyskać więcej informacji, zobacz [przy użyciu setjmp i longjmp](../../cpp/using-setjmp-longjmp.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`setjmp`|\<setjmp.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_fpreset —](../../c-runtime-library/reference/fpreset.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [longjmp](../../c-runtime-library/reference/longjmp.md)   
 [_setjmp3](../../c-runtime-library/setjmp3.md)