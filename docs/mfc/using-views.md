---
title: "Korzystanie z widoków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interacting with users and role of view class [MFC]
- drawing [MFC], data
- rendering data
- view classes [MFC], role in managing user interaction
- CView class [MFC], view architecture
- MFC, views
- views [MFC], using
- painting data
- user input [MFC], interpreting through view class [MFC]
- view classes [MFC], role in displaying application data
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 633bd52b64ba6c4c507867320585b8bc513e80c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-views"></a>Używanie widoków
Obowiązki widoku są do wyświetlenia danych dokumentu graficznie dla użytkownika i aby zaakceptować i interpretowanie danych wprowadzonych przez użytkownika jako operacje w dokumencie. Zadania w klasie widoku pisaniu są:  
  
-   Zapis w klasie widoku [OnDraw](../mfc/reference/cview-class.md#ondraw) funkcji członkowskiej, która renderuje dane dokumentu.  
  
-   Podłącz odpowiednie komunikaty systemu Windows i obiekty interfejsu użytkownika, takie jak elementy menu do funkcji Członkowskich obsługi wiadomości w klasie widoku.  
  
-   Implementuje te programy obsługi interpretowanie danych wprowadzonych przez użytkownika.  
  
 Ponadto należy zastąpić inne `CView` funkcji Członkowskich w klasie pochodnej widoku. W szczególności można zastąpić [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) wykonać specjalne inicjowania w widoku i [OnUpdate](../mfc/reference/cview-class.md#onupdate) celu żadnych specjalnego przetwarzania potrzebne tuż przed widoku ponownie rysuje sam. Wielostronicowe dokumentów, należy również zmienić [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) zainicjować okno dialogowe Drukuj o liczbie stron i inne informacje. Aby uzyskać więcej informacji na temat zastępowania `CView` funkcji członkowskiej, zobacz klasę [CView](../mfc/reference/cview-class.md) w *odwołania MFC*.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Pochodne klasy widoków dostępne w MFC](../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Rysowanie w widoku](../mfc/drawing-in-a-view.md)  
  
-   [Interpretowanie danych wejściowych użytkownika za pośrednictwem widoku](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [Rola widoku w drukowaniu](../mfc/role-of-the-view-in-printing.md)  
  
-   [Przewijanie i skalowanie widoków](../mfc/scrolling-and-scaling-views.md)  
  
-   [Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura dokument/widok](../mfc/document-view-architecture.md)   
 [Klasa CFormView](../mfc/reference/cformview-class.md)   
 [Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)   
 [Pomijanie mechanizmu serializacji](../mfc/bypassing-the-serialization-mechanism.md)

