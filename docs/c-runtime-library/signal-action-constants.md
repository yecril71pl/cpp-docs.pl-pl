---
title: "Stałe akcji sygnałów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SIG_IGN
- SIG_DFL
dev_langs: C++
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 256f11d3f8daa8a00e70e24aa19c31b71413c13c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="signal-action-constants"></a>Stałe akcji sygnałów
Akcję wykonywaną po odebraniu sygnału przerwania zależy od wartości `func`.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <signal.h>  
```  
  
## <a name="remarks"></a>Uwagi  
 `func` Argument musi być adresu funkcji lub jeden z manifestu stałe wymienionych poniżej i zdefiniowanych w sygnału. H.  
  
 `SIG_DFL`  
 Używa domyślnego systemu odpowiedzi. Jeśli program wywołujący używa strumień we/wy, buforów utworzone przez biblioteki wykonawczej nie są opróżniane.  
  
 `SIG_IGN`  
 Ignoruje sygnał przerwania. Nigdy nie należy podać tę wartość `SIGFPE`, ponieważ zmiennoprzecinkowy stan procesu zostanie pozostawiony niezdefiniowany.  
  
 `SIG_SGE`  
 Wskazuje, że wystąpił błąd podczas sygnału.  
  
 `SIG_ACK`  
 Wskazuje, że otrzymano potwierdzenia.  
  
 `SIG_ERR`  
 Typ zwracany z sygnał wskazujący błąd wystąpił.  
  
## <a name="see-also"></a>Zobacz też  
 [sygnał](../c-runtime-library/reference/signal.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)