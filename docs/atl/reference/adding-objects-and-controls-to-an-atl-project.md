---
title: "Dodawanie do projektu ATL obiektów i kontrolki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.appwiz.ATL.controls
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e01b39eb7393d171b2c1fb30193810f62be85b99
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Dodawanie obiektów i kontroli do projektu ATL
Można użyć jednego z kreatorów kodu ATL można dodać obiektu lub formantu do projektów ATL i MFC — na podstawie. Dla każdego obiektu modelu COM lub formantu można dodać, Kreator generuje .cpp i pliki .h, a także pliku .rgs obsługi opartych na skryptach rejestru. Następujących kreatorów kodu ATL są dostępne w programie Visual Studio:  
  
||||  
|-|-|-|  
|[Prosty obiekt ATL](../../atl/reference/atl-simple-object-wizard.md)|[Okno dialogowe ATL](../../atl/reference/atl-dialog-wizard.md)|[Formant ATL](../../atl/reference/atl-control-wizard.md)|  
|[Strony właściwości ATL](../../atl/reference/atl-property-page-wizard.md)|[Składnik strony Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)|[Konsumenta ATL OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md)|  
|[Dodaj obsługę ATL do MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[ATL COM + 1.0 Kreator składników stron ASP](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Dostawca ATL OLE DB](../../atl/reference/atl-ole-db-provider-wizard.md)|  
  
> [!NOTE]
>  Przed dodaniem obiekt ATL do projektu, należy przejrzeć szczegóły i wymagania dla obiekt w jego powiązanych tematów Pomocy.  
  
### <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Aby dodać obiekt lub formantu przy użyciu Kreator formantu ATL  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij przycisk **Dodaj** z menu skrótów. Kliknij przycisk **Dodaj klasę**.  
  
     [Dodaj klasę](../../ide/add-class-dialog-box.md) zostanie wyświetlone okno dialogowe.  
  
2.  Z folderu ATL zaznaczonego w okienku kategorii wybierz obiekt, aby wstawić z okienka Szablony. Kliknij przycisk **Otwórz**. Zostanie wyświetlony Kreator kodu dla wybranego obiektu.  
  
    > [!NOTE]
    >  Jeśli chcesz dodać obiekt ATL do projektu MFC, należy dodać obsługę ATL do istniejącego projektu. Aby to zrobić, postępując zgodnie z instrukcjami w [Dodawanie obsługi ATL do projektu MFC Your](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
     Alternatywnie próbie Dodaj obiekt ATL do projektu MFC bez wcześniej Dodawanie obsługi ATL Visual Studio wyświetli monit o określenie, czy mają obsługi ATL dodanej do projektu. Kliknij przycisk **tak** Dodaj obsługę ATL do projektu i Otwórz kreatora ATL wybrane.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)   
 [Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)   
 [Tworzenie projektów pulpitu za pomocą kreatorów aplikacji](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Podstawowe informacje na temat ATL COM — obiekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [Programowanie za pomocą ALT i C Run-Time kodu](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)

