---
title: "Implementacja punktu połączenia (Visual C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2e377b3945f85d1c5759344992046e9fafb16103
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-a-connection-point-visual-c"></a>Implementacja punktu połączenia (Visual C++)
Do zaimplementowania punktu połączenia za pomocą Kreatora punktu połączenia wdrożenia, musi mieć projekt został utworzony jako aplikacji ATL COM lub aplikacji MFC, która zawiera obsługę ATL. Można użyć [Kreator projektu ATL](../atl/reference/atl-project-wizard.md) Aby utworzyć aplikację ATL lub [Dodaj obiekt ATL do aplikacji MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) ATL Obsługa aplikacji MFC.  
  
> [!NOTE]
>  Aby dowiedzieć się, jak implementacja punktów połączeń dla projektu MFC, zobacz [punkty połączenia](../mfc/connection-points.md).  
  
 Po utworzeniu projektu, do zaimplementowania punktu połączenia, najpierw należy dodać obiekt ATL. Zobacz [Dodawanie obiektów i kontroli w celu Projekt ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) listę kreatorów, które dodać obiekty do projektu ATL.  
  
> [!NOTE]
>  Kreator nie obsługuje okien dialogowych ATL, utworzone za pomocą serwera ATL obiekty wydajności i liczniki wydajności usługi XML sieci Web.  
  
 Obiekt składnika (źródło) mogą uwidaczniać punktu połączenia dla każdego z jego interfejsy wychodzących. Każdy interfejs wychodzącej może być zaimplementowany przez klienta do obiektu (zbiornika). Aby uzyskać więcej informacji, zobacz [punkty połączenia ATL](../atl/atl-connection-points.md).  
  
### <a name="to-implement-a-connection-point"></a>Do zaimplementowania punktu połączenia  
  
1.  W widoku klas kliknij prawym przyciskiem myszy nazwę klasy dla obiekt ATL.  
  
2.  Kliknij przycisk **Dodaj** z menu skrótów, a następnie kliknij przycisk **Dodaj punkt połączenia** do wyświetlenia [Kreator implementacji punktu połączenia](../ide/implement-connection-point-wizard.md).  
  
3.  Wybierz interfejsy punktu połączenia, aby zaimplementować z bibliotek odpowiedniego typu, a następnie kliknij przycisk **Zakończ**.  
  
4.  W widoku klas Sprawdź klasy serwera proxy, tworzone dla każdego punktu połączenia. Klasy są wyświetlane jako CProxy*InterfaceName*\<T > i pochodne [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).  
  
5.  Kliknij dwukrotnie klasy punktu połączenia do wyświetlania definicji klasy punktu połączenia.  
  
    -   W przypadku zastosowania punktu połączenia dla interfejsu własny projekt, pojawi się następujący definicji  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         Jeśli można zaimplementować interfejsu lokalnego, metody i właściwości są wyświetlane w treści klasy.  
  
    -   Jeśli implementacji punktu połączenia dla interfejsu innego definicja zawiera metody interfejsu, każdy poprzedzony `Fire_`.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie punktów połączenia do obiektu](../atl/adding-connection-points-to-an-object.md)