---
title: "&lt;przyszłe&gt; wyliczenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 835abafde46858bd108dfa648a246345bd254eaf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltfuturegt-enums"></a>&lt;przyszłe&gt; wyliczenia
||||  
|-|-|-|  
|[future_errc —](#future_errc)|[future_status —](#future_status)|[Uruchamianie](#launch)|  
  
##  <a name="future_errc"></a>future_errc — wyliczenie  
 Dostarcza nazw symbolicznych wszystkie błędy, które są zgłaszane przez [future_error —](../standard-library/future-error-class.md) klasy.  
  
future_errc klasy — {broken_promise, future_already_retrieved, promise_already_satisfied, no_state};  
  
##  <a name="future_status"></a>future_status — wyliczenie  
 Dostarcza nazw symbolicznych z powodów zwracających w funkcji czasu oczekiwania.  
  
```
enum future_status{    ready,
    timeout,
 deferred};
```  
  
##  <a name="launch"></a>Launch — wyliczenie  
 Reprezentuje typ maski, który opisuje możliwe tryby funkcji szablonu [async](../standard-library/future-functions.md#async).  
  
Klasa uruchamiania {asynchroniczne, odroczone};  
  
## <a name="see-also"></a>Zobacz też  
 [\<przyszłe >](../standard-library/future.md)



