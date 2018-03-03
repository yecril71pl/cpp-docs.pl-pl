---
title: "sygnał — stałe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
dev_langs:
- C++
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e47e3e7bce5a41e055f251d906ec72d98c5b285
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="signal-constants"></a>sygnał — Stałe
## <a name="syntax"></a>Składnia  
  
```  
#include <signal.h>  
```  
  
## <a name="remarks"></a>Uwagi  
 `sig` Argument musi być jedną z manifestu stałe wymienionych poniżej (zdefiniowanego w sygnału. H).  
  
 `SIGABRT`  
 Przerwania pracy. Domyślne działanie kończy program wywołujący z kodem zakończenia 3.  
  
 `SIGABRT_COMPAT`  
 Taka sama jak sigabrt —. Aby zapewnić zgodność z innych platform.  
  
 `SIGFPE`  
 Błąd liczb zmiennoprzecinkowych, takich jak przepełnienia, dzielenie przez zero lub nieprawidłowa operacja. Domyślne działanie kończy program wywołujący.  
  
 `SIGILL`  
 Niedozwolona instrukcja. Domyślne działanie kończy program wywołujący.  
  
 `SIGINT`  
 Przerwanie klawisze CTRL + C. Domyślne działanie kończy program wywołujący z kodem zakończenia 3.  
  
 `SIGSEGV`  
 Dostępu do magazynu niedozwolone. Domyślne działanie kończy program wywołujący.  
  
 `SIGTERM`  
 Zakończenie żądania wysyłane do programu. Domyślne działanie kończy program wywołujący z kodem zakończenia 3.  
  
 `SIG_ERR`  
 Typ zwracany z sygnał wskazujący błąd wystąpił.  
  
## <a name="see-also"></a>Zobacz też  
 [sygnał](../c-runtime-library/reference/signal.md)   
 [Zgłoś](../c-runtime-library/reference/raise.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)