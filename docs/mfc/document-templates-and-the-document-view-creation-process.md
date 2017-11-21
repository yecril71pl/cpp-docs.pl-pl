---
title: "Szablony dokumentów i proces tworzenia dokumentu widoku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- icons, for multiple document templates
- document templates [MFC], and views
- document/view architecture [MFC], creating document/view
- single document template
- MFC, document templates
- multiple document template
- CDocTemplate class [MFC]
- templates [MFC], document templates
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6636685e45f4ba65460da5ff0a67f5c023ba1d0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="document-templates-and-the-documentview-creation-process"></a>Szablony dokumentów i proces tworzenia dokumentu/widoku
Do zarządzania złożony proces tworzenia dokumentów z ich skojarzonych widoków i okien ramowych, używane są dwie klasy szablonów dokumentów platformę: [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) dla SDI — aplikacje i [CMultiDocTemplate ](../mfc/reference/cmultidoctemplate-class.md) dla aplikacji MDI. A `CSingleDocTemplate` można utworzyć i zapisać jeden dokument jednego typu naraz. A `CMultiDocTemplate` przechowuje listę wiele otwarte dokumenty jednego typu.  
  
 Niektóre aplikacje obsługują wiele typów dokumentów. Na przykład aplikacja może obsługiwać dokumentów tekstu i grafiki, dokumenty. W aplikacji gdy użytkownik wybierze polecenie Nowy w menu Plik okno dialogowe zawiera listę możliwych nowych typów dokumentu, aby otworzyć. Dla każdego typu obsługiwanych dokumentu aplikacja używa obiektu szablonu dokumentu distinct. Poniższa ilustracja przedstawia konfigurację aplikacji MDI obsługuje dwa typy dokumentu, który zawiera kilka otwarte dokumenty.  
  
 ![MDI aplikacji, która ma dwa typy dokumentu](../mfc/media/vc387h1.gif "vc387h1")  
Aplikacja MDI z dwóch typów dokumentów  
  
 Szablony dokumentów są tworzone i obsługiwane przez obiekt aplikacji. Jednym z kluczowych zadań wykonywanych podczas aplikacji `InitInstance` funkcji jest utworzyć co najmniej jeden szablon dokumentu odpowiedniego typu. Ta funkcja jest opisana w [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md). Obiekt aplikacji przechowuje wskaźnik do każdego szablonu dokumentu w jego Lista szablonów i zawiera interfejs umożliwiający dodanie szablonów dokumentów.  
  
 Musisz obsługuje dwa lub więcej typów dokumentów, należy dodać dodatkowe wywołanie [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) dla każdego typu dokumentu.  
  
 Ikona jest zarejestrowany dla każdego szablonu dokumentu, na podstawie jego pozycji na liście aplikacji szablonów dokumentów. Kolejność szablonów dokumentów jest określana przez kolejność są dodawane wywołania `AddDocTemplate`. MFC przyjęto założenie, że ikona aplikacji jest pierwszym zasobu ikony w aplikacji, dalej zasobu ikony jest pierwsza ikona dokumentu i tak dalej.  
  
 Na przykład szablon dokumentu jest trzeci trzech dla aplikacji. Jeśli w aplikacji w indeksie 3 jest zasobu ikony, tego ikona jest stosowana dla szablonu dokumentów. Jeśli nie, ikony pod indeksem 0 jest używany jako domyślny.  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)   
 [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)   
 [Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)   
 [Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)   
 [Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)

