---
title: Stałe akcji sygnałów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- SIG_IGN
- SIG_DFL
dev_langs:
- C++
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b6f645d474e697bf662a5dd63973dd54c329eb9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
 [Sygnał](../c-runtime-library/reference/signal.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)