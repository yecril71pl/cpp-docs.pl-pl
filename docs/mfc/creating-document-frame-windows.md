---
title: Tworzenie okien ramowych dokumentu | Dokumentacja firmy Microsoft
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
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9098026c1a38f8e60093415ba1c5a2b3678b64d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-document-frame-windows"></a>Tworzenie okien ramowych dokumentu
[Tworzenie dokumentu/widoku](../mfc/document-view-creation.md) przedstawia sposób [cdoctemplate —](../mfc/reference/cdoctemplate-class.md) obiektu organizuje tworzenie okien ramowych dokumentu, a widok i łącząc je do wszystkich elementów. Trzy [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) argumenty `CDocTemplate` Konstruktor Określ okno ramowe, klasy dokumentów i widoków tworzone przez szablon dokumentu dynamicznie w odpowiedzi na polecenia użytkownika, takie jak nowe polecenie do pliku menu lub nowe okno polecenia menu okna MDI. Szablon dokumentu przechowuje tych informacji do późniejszego użycia podczas tworzenia ramkę okna do widoku i dokumentu.  
  
 Dla [runtime_class —](../mfc/reference/run-time-object-model-services.md#runtime_class) mechanizmu działał prawidłowo, Twoje pochodne klasy okien ramowych musi być zadeklarowany ze [declare_dyncreate —](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) makra. Wynika to z faktu w ramach musi utworzyć dokumentu przy użyciu mechanizmu dynamicznej konstrukcji klasy okien ramowych `CObject`.  
  
 Gdy użytkownik wybierze polecenie, które tworzy dokument, struktura wywołuje na szablonu dokumentu, można utworzyć obiektu dokumentu, jego widoku i okno ramowe, która będzie wyświetlana w widoku. Podczas tworzenia okna ramki dokumentu, szablon dokumentu tworzy obiekt odpowiedniej klasy — klasą pochodną [cframewnd —](../mfc/reference/cframewnd-class.md) aplikacji SDI lub z [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dla MDI aplikacja. Struktura następnie wywołuje obiekt okno ramowe [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) funkcji członkowskiej można pobrać informacji o tworzeniu z zasobów i utworzyć okno systemu Windows. Platformę dołącza uchwytu okna do obiektu okna ramowego. Następnie tworzy widok jako okna podrzędnego okna ramowe dokumentów.  
  
 Należy zachować ostrożność przy podejmowaniu decyzji [kiedy inicjować](../mfc/when-to-initialize-cwnd-objects.md) Twojego `CWnd`-pochodzi z obiektu.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Wyprowadzanie klasy z obiektu CObject (jego mechanizm tworzenia dynamicznych)](../mfc/deriving-a-class-from-cobject.md)  
  
-   [Tworzenie dokumentu/widoku (szablony i tworzenie okien ramowych)](../mfc/document-view-creation.md)  
  
-   [Niszczenie okien ramowych](../mfc/destroying-frame-windows.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie okien ramowych](../mfc/using-frame-windows.md)

