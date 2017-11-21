---
title: "_local_unwind2 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _local_unwind2
apilocation:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- _local_unwind2
- local_unwind2
dev_langs: C++
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8ad37d66e0e73e7ee75e2c44869c59c545025bd6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="localunwind2"></a>_local_unwind2
Funkcji CRT wewnętrznej. Uruchamia wszystkie programy obsługi zakończenia, które są wymienione w tabeli wskazany zakres.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _local_unwind2(  
   PEXCEPTION_REGISTRATION xr,  
   int stop  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`xr`  
 Rekord rejestracji jest skojarzony z tabelą jednego zakresu.  
  
 [in]`stop`  
 Poziom leksykalne, która wskazuje, gdzie `_local_unwind2` powinna zostać przerwana.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana tylko przez środowisko wykonawcze. Nie wywołuj metody w kodzie.  
  
 Gdy ta metoda jest wykonywana programy obsługi zakończenia, zaczynała się na bieżącym poziomie leksykalne i działa drodze się w poziomach leksykalne, dopóki nie osiągnie poziom które jest określane przez `stop`. Nie wykonuj programy obsługi zakończenia na poziomie, który jest wskazywany przez `stop`.  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)