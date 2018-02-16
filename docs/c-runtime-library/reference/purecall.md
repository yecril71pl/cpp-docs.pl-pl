---
title: "_purecall — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _purecall
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
dev_langs:
- C++
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c19324cde907f31ab18a312f3039c2da7a3a40c7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="purecall"></a>_purecall
Obsługę błędów wywołanie czystej funkcji wirtualnej domyślne. Kompilator generuje kod, aby wywołanie tej funkcji, gdy jest wywoływana przez pure wirtualną funkcją członkowską.  
  
## <a name="syntax"></a>Składnia  
  
```  
extern "C" int __cdecl _purecall();  
```  
  
## <a name="remarks"></a>Uwagi  
 `_purecall` Funkcja jest specyficzne dla firmy Microsoft szczegół implementacji kompilator Microsoft Visual C++. Ta funkcja nie jest przeznaczony do bezpośredniego wywoływania przez kod i ma nie ma publicznego nagłówka deklaracji. Jest opisane w tym miejscu ponieważ jest on publiczny eksportu biblioteki C Runtime.  
  
 Wywołanie czystej funkcji wirtualnej występuje błąd, ponieważ ma ona żadnej implementacji. Kompilator generuje kod, aby wywołać `_purecall` funkcji obsługi błędu, gdy jest wywoływana czystej funkcji wirtualnej. Domyślnie `_purecall` kończy program. Przed zakończeniem, `_purecall` wywołuje funkcję `_purecall_handler` działać, jeśli został zdefiniowany dla procesu. Można zainstalować własnych funkcji obsługi błędu dla wywołań czystej funkcji wirtualnej, aby wykryć je do debugowania lub celów raportowania. Aby korzystać z własnych program obsługi błędów, tworzy funkcję, która ma `_purecall_handler` podpisu, następnie użyć [_set_purecall_handler —](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) dokonanie bieżący program obsługi.  
  
## <a name="requirements"></a>Wymagania  
 `_purecall` Funkcja nie zawiera deklaracji nagłówka. `_purecall_handler` Element typedef jest zdefiniowany w \<stdlib.h >.  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_purecall_handler, _set_purecall_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)