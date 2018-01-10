---
title: Ustawienia aplikacji, ATL Kreator projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.appwiz.atl.com.appset
dev_langs: C++
helpviewer_keywords: ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12b7e383716d7cfa330bdfdebe21c33550669cc2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="application-settings-atl-project-wizard"></a>Ustawienia aplikacji, Kreator projektu ATL
Użyj **ustawienia aplikacji** strony Kreator projektu ATL do projektu i dodawanie podstawowych funkcji do nowy projekt ATL.  
  
## <a name="server-type"></a>Typ serwera  
 Wybierz jedną z trzech typów serwerów:  
  
 **Biblioteki dołączanej (dynamicznie DLL)**  
 Wybierz, aby utworzyć server wewnątrzprocesowe.  
  
 **Pliki wykonywalne (EXE)**  
 Wybierz, aby utworzyć lokalnego serwera poza procesem. Ta opcja nie zezwala na obsługę MFC lub COM + 1.0. Nie zezwala na scalanie kodu serwera proxy/stub.  
  
 **Usługi (EXE)**  
 Wybierz, aby utworzyć aplikację systemu Windows, która działa w tle podczas uruchamiania systemu Windows. Tej opcji nie zezwalaj na obsługę MFC lub COM + 1.0 lub nie zezwala na scalanie kodu serwera proxy/stub.  
  
## <a name="additional-options"></a>Dodatkowe opcje  
  
> [!NOTE]
>  Wszystkie dodatkowe opcje są dostępne dla projektów biblioteki DLL tylko.  
  
 **Zezwalaj na scalanie kodu serwera proxy/stub**  
 Wybierz **Zezwalaj na scalanie kodu serwera proxy/stub** pole wyboru dla wygody, gdy wymagana jest przekazywanie interfejsów. Ta opcja umieszcza kod serwera proxy i skrótowych generowanych przez MIDL w tym samym pliku wykonywalnego jako serwer.  
  
 **Obsługa MFC**  
 Wybierz, aby określić, że obiekt zawiera obsługę MFC. Ta opcja łączy projektu biblioteki MFC, aby uzyskać dostępu do żadnego z klasy i funkcje, które zawierają.  
  
 **Obsługa modelu COM + 1.0**  
 Wybierz, aby zmodyfikować ustawienia kompilacji projektu do obsługi składników modelu COM + 1.0. Oprócz standardowych listę bibliotek Kreator dodaje comsvcs.lib biblioteki specyficzne dla składnika modelu COM + 1.0  
  
 Ponadto mtxex.dll to opóźnienie ładowane w systemie hosta, gdy aplikacja jest uruchamiana.  
  
-   **Obsługuje rejestratora składników** Projekt ATL zawiera obsługę składników modelu COM + 1.0, należy ustawić tę opcję. Rejestrator składników umożliwia obiektu modelu COM + 1.0 do uzyskiwania listy składników, zarejestrować komponenty lub wyrejestrować komponenty (indywidualnie lub jednorazowo).  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)   
 [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)   
 [Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)

