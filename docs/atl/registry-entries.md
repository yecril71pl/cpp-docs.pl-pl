---
title: Wpisy rejestru (ATL) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: faef0ca0c1c9c4c2986a039b8b1a26517641acd0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="registry-entries"></a>Wpisy rejestru
DCOM wprowadzono pojęcie identyfikatorów aplikacji (AppIDs), które grupy opcji konfiguracji dla co najmniej jeden obiekt modelu DCOM w centralnej lokalizacji w rejestrze. Identyfikator AppID można określić, wprowadzając wartości AppID o nazwie wartości na podstawie identyfikatora CLSID obiektu.  
  
 Domyślnie usługa wygenerowany ATL używa jego identyfikator CLSID jako identyfikatora GUID dla jego identyfikator aplikacji. W obszarze `HKEY_CLASSES_ROOT\AppID`, można określić wpisy specyficzne dla modelu DCOM. Początkowo istnieją dwa wpisy:  
  
-   `LocalService`, wartość jest taka sama jak nazwa usługi. Jeśli ta wartość istnieje, jest ona używana zamiast `LocalServer32` klucza w obszarze identyfikatora CLSID.  
  
-   `ServiceParameters`, z wartością równą `-Service`. Ta wartość określa parametry, które zostaną przekazane do usługi podczas jej uruchamiania. Należy pamiętać, że te parametry są przekazywane do usługi `ServiceMain` funkcji nie `WinMain`.  
  
 Usługi modelu DCOM również musi utworzyć inny klucz w obszarze `HKEY_CLASSES_ROOT\AppID`. Ten klucz jest taka sama jak nazwa pliku EXE, a także pełni rolę odsyłaczy, ponieważ zawiera on wartość AppID wskazujący wpisy AppID.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi](../atl/atl-services.md)

