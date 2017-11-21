---
title: "Dodawanie strony właściwości ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a7c1d7ae11873c2bc47f1bb4a7a2439768e8347b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="adding-an-atl-property-page"></a>Dodawanie strony właściwości ATL
Na stronie właściwości Active Template Library (ATL) należy dodać do projektu, projektu musi być utworzony jako aplikacji ATL lub aplikacji z obsługą ATL MFC. Można użyć [Kreator projektu ATL](../../atl/reference/atl-project-wizard.md) do tworzenia aplikacji ATL lub [Dodaj obiekt ATL do aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) ATL Obsługa aplikacji MFC.  
  
 Jeśli dodajesz strony właściwości kontrolki musi obsługiwać formantu [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) interfejsu. Domyślnie ten interfejs jest na liście pochodnym formantu klasy, gdy użytkownik [Tworzenie formantu ATL](../../atl/reference/adding-an-atl-control.md) przy użyciu [Kreator formantu ATL](../../atl/reference/atl-control-wizard.md).  
  
> [!NOTE]
>  Jeśli nie ma Twojej klasy kontrolki [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) liście pochodnym, należy go dodać ręcznie.  
  
### <a name="to-add-an-atl-property-page-to-your-project"></a>Aby dodać stronę właściwości ATL do projektu  
  
1.  W jednym **Eksploratora rozwiązań** lub [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), kliknij prawym przyciskiem myszy nazwę projektu, do której chcesz dodać stronę właściwości ATL.  
  
2.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj klasę**.  
  
3.  W [Dodaj klasę](../../ide/add-class-dialog-box.md) kliknij okno dialogowe, w okienku szablonów **stronę właściwości ATL** , a następnie kliknij przycisk **Otwórz** do wyświetlenia [KreatorstronywłaściwościATL](../../atl/reference/atl-property-page-wizard.md).  
  
 Po utworzeniu strony właściwości formantu, należy podać [PROP_PAGE](property-map-macros.md#prop_page) wpis w mapie właściwości formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości](../../atl/atl-com-property-pages.md)   
 [Podstawowe informacje na temat ATL COM — obiekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [Przykład: Implementacja strony właściwości](../../atl/example-implementing-a-property-page.md)

