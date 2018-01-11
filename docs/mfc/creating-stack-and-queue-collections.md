---
title: "Tworzenie kolekcji stosów i kolejek | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC collection classes [MFC], stack collections
- collections, stack
- stack
- collection classes [MFC], creating
- queue collections
- MFC collection classes [MFC], queue collections
- stack collections
- collections, queue
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dd3c4d587f64fc89bf25cfd127e6b7efc490df8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-stack-and-queue-collections"></a>Tworzenie kolekcji stosów i kolejek
W tym artykule opisano sposób tworzenia inne struktury danych, takich jak [stosy](#_core_stacks) i [kolejek](#_core_queues), z MFC lista klas. W przykładach użyto klasy pochodzące od `CList`, ale można użyć `CList` bezpośrednio, chyba że konieczne jest dodanie funkcji.  
  
##  <a name="_core_stacks"></a>Stosy  
 Ponieważ kolekcji standardowych listy head oraz tail, jest łatwo utworzyć kolekcję pochodnej listy, która symuluje zachowanie stosu ostatnich w pierwszym poza. Stos przypomina stosu zasobników w kawiarnia. Gdy zasobników są dodawane do stosu, przejdź na szczycie stosu. Ostatniego na pasku zadań, dodane jest pierwsze do usunięcia. Funkcje Członkowskie kolekcji listy `AddHead` i `RemoveHead` może służyć do dodania i usunięcia elementów w szczególności z węzła głównego z listy; w związku z tym najbardziej ostatnio dodany element to pierwszy do usunięcia.  
  
#### <a name="to-create-a-stack-collection"></a>Aby utworzyć kolekcję stosu  
  
1.  Klasa wyprowadzona z nowej listy na jednym z istniejących lista klas MFC i dodać więcej funkcji elementów członkowskich do obsługi funkcji operacji stosu.  
  
     W poniższym przykładzie przedstawiono sposób dodawania funkcji Członkowskich push elementów na stosie rzut oka na górnego elementu stosu, i pop górny element ze stosu:  
  
     [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]  
  
 Należy pamiętać, że to rozwiązanie przedstawia podstawową `CObList` klasy. Użytkownik może wywołać dowolną `CObList` funkcji członkowskiej, czy warto stosu lub nie.  
  
##  <a name="_core_queues"></a>Kolejki  
 Ponieważ kolekcji standardowych listy head oraz tail, również jest łatwo utworzyć kolekcję pochodnej listy, która symuluje zachowanie kolejki pierwszy w pierwszym poza. Kolejka jest jak linia życia osób w kawiarnia. Pierwsza osoba w wierszu jest pierwszy ma być obsługiwana. Ponieważ pochodzą więcej osób, przejdź do końca wiersza oczekiwania ich Włącz. Funkcje Członkowskie kolekcji listy `AddTail` i `RemoveHead` można dodać i usunąć elementy w szczególności head lub tail listy; w związku z tym maksymalnie niedawno dodano element jest zawsze ostatni usunięcie.  
  
#### <a name="to-create-a-queue-collection"></a>Aby utworzyć kolekcję kolejki  
  
1.  Pochodzić z jednej z klas wstępnie zdefiniowanej listy dostarczane z Microsoft Foundation Class Library nową klasę listy i dodać więcej funkcji elementów członkowskich do obsługi semantykę operacji kolejki.  
  
     W poniższym przykładzie pokazano, jak dołączyć funkcje Członkowskie Dodaj element na końcu kolejki i uzyskać elementu z przodu kolejki.  
  
     [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje](../mfc/collections.md)

