---
title: DCOMCNFG | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DCOMCNFG
dev_langs: C++
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f40b372666ba2b623450eb0e58a6c0ff372559ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dcomcnfg"></a>DCOMCNFG
**DCOMCNFG** to narzędzie systemu Windows NT 4.0, które można skonfigurować różne ustawienia specyficzne dla modelu DCOM w rejestrze. **DCOMCNFG** okno ma trzy strony: domyślne zabezpieczeń, właściwości domyślne i aplikacji. W systemie Windows 2000 czwartej stronie domyślne protokołów jest obecny.  
  
## <a name="default-security-page"></a>Domyślna strona zabezpieczeń  
 Strona domyślnych zabezpieczeń służy do określenia domyślnych uprawnień do obiektów w systemie. Strona domyślna zabezpieczeń zawiera trzy sekcje: dostępu, uruchamiania i konfiguracji. Aby zmienić wartości domyślne sekcji, kliknij odpowiedni **Edytuj domyślne** przycisku. Te ustawienia domyślne zabezpieczeń są przechowywane w kluczu rejestru `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`.  
  
## <a name="default-protocols-page"></a>Domyślna strona Protokoły  
 Ta strona zawiera zestaw protokołów sieciowych dostępnych dla modelu DCOM na tym komputerze. Kolejność odzwierciedla priorytet, w którym będą używane; pierwszy na liście ma najwyższy priorytet. Protokoły można dodać lub usunąć z tej strony.  
  
## <a name="default-properties-page"></a>Domyślne właściwości strony  
 Na stronie właściwości domyślne należy wybrać **Włącz model obiektów rozproszonych COM na tym komputerze** pole wyboru, jeśli chcesz, aby klienci w innych maszyn do obiektów COM dostępu uruchomiona na tym komputerze. Wybranie tej opcji ustawia `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` do wartości `Y`.  
  
## <a name="applications-page"></a>Strona aplikacji  
 Możesz zmienić ustawienia określonego obiektu ze strony aplikacji. Wybierz aplikację z listy i kliknij przycisk **właściwości** przycisku. Okno właściwości zawiera pięć stron:  
  
-   Strony Ogólne potwierdza aplikacji, którą użytkownik pracuje z.  
  
-   Na stronie Lokalizacja można określić, gdzie należy uruchomić aplikację, kiedy klient wywołuje `CoCreateInstance` na odpowiedni identyfikator CLSID. W przypadku wybrania **Uruchom aplikację na następującym komputerze** pole wyboru i wpisz nazwę komputera, a następnie `RemoteServerName` wartość jest dodawana pod identyfikatorem AppID dla tej aplikacji. Wyczyszczenie **Uruchom aplikację na tym komputerze** zmienia nazwę pola wyboru `LocalService` do wartości `_LocalService` i tym samym, wyłącza je.  
  
-   Strona zabezpieczeń jest podobna do zabezpieczenia domyślna strona została znaleziona w **DCOMCNFG** okna, z wyjątkiem tego, że te ustawienia dotyczą tylko w bieżącej aplikacji. Ponownie te ustawienia są przechowywane w obszarze AppID dla tego obiektu.  
  
-   Na stronie Określ identyfikuje użytkownika, który jest używany do uruchamiania aplikacji.  
  
-   Strona punkty końcowe zawiera zestaw protokołów i punktów końcowych dostępnych do użycia przez klientów na wybranym serwerze modelu DCOM.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi](../atl/atl-services.md)

