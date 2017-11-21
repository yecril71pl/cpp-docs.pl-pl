---
title: 'Kontenery: Implementowanie kontenera | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fe58203bb6f9b5e8aa2c793ac5f4f21a5819df85
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="containers-implementing-a-container"></a>Kontenery: implementowanie kontenera
W tym artykule przedstawiono sposób stosowania kontener i wskazaniu inne artykuły, które zapewniają bardziej szczegółowych wyjaśnień dotyczących implementowania kontenerów. Wyświetla również niektórych funkcji opcjonalnych OLE, który chcesz wdrożyć, a artykuł opisujący te funkcje.  
  
#### <a name="to-prepare-your-cwinapp-derived-class"></a>Aby przygotować klasy pochodnej CWinApp  
  
1.  Inicjowanie bibliotek OLE przez wywołanie metody **afxoleinit —** w `InitInstance` funkcję elementu członkowskiego.  
  
2.  Wywołanie `CDocTemplate::SetContainerInfo` w `InitInstance` można przypisać do menu skrótów zasoby używane w przypadku element osadzony aktywacji w miejscu. Aby uzyskać więcej informacji na ten temat, zobacz [aktywacji](../mfc/activation-cpp.md).  
  
 Te funkcje są dostępne dla zostanie automatycznie podczas tworzenia aplikacji kontenera za pomocą Kreatora aplikacji MFC. Zobacz [tworzenia Program MFC EXE](../mfc/reference/mfc-application-wizard.md).  
  
#### <a name="to-prepare-your-view-class"></a>Aby przygotować klasy widoku  
  
1.  Śledzić różne elementy wybrane dzięki utrzymywaniu wskaźnik lub listy wskaźników, jeśli obsługuje wyboru wielokrotnego, do wybranych elementów. Twoje `OnDraw` funkcja należy narysować wszystkie elementy OLE.  
  
2.  Zastąpienie `IsSelected` do sprawdzenia, czy element przekazany do niego jest aktualnie zaznaczone.  
  
3.  Implementowanie **OnInsertObject** obsługi wiadomości, aby wyświetlić **Wstaw obiekt** okno dialogowe.  
  
4.  Implementowanie `OnSetFocus` komunikat obsługi na przesyłanie fokus z widoku do aktywnego OLE w miejscu osadzonego elementu.  
  
5.  Implementowanie `OnSize` obsługi wiadomości, aby informować OLE osadzonych elementów należy zmienić jego prostokąta, aby odzwierciedlić zmianę rozmiaru jego zawierający widok.  
  
 Ponieważ stosowania tych funkcji znacznie różni się w jednej aplikacji do następnego, Kreator aplikacji udostępnia podstawową implementację. Prawdopodobnie należy dostosować te funkcje można pobrać aplikację do poprawnego działania. Aby na przykład, zobacz [kontenera](../visual-cpp-samples.md) próbki.  
  
#### <a name="to-handle-embedded-and-linked-items"></a>Do obsługi elementy osadzone i połączone  
  
1.  Klasa wyprowadzona z [COleClientItem](../mfc/reference/coleclientitem-class.md). Obiekty ta klasa reprezentuje elementy, które zostały osadzone w lub połączony z dokumentu OLE.  
  
2.  Zastąpienie **OnChange**, `OnChangeItemPosition`, i `OnGetItemPosition`. Te funkcje uchwyt zmiany rozmiaru, pozycjonowanie i modyfikowanie elementy osadzone i połączone.  
  
 Kreator aplikacji będą pochodzić klasy dla Ciebie, ale prawdopodobnie będzie konieczne zastąpienie **OnChange** i inne funkcje wymienione z nim w kroku 2 w poprzedniej procedurze. Szkielet implementacji konieczne można dostosować w przypadku większości aplikacji, ponieważ te funkcje są implementowane inaczej z jednej aplikacji do następnego. Przykłady tego, zobacz przykłady MFC [DRAWCLI](../visual-cpp-samples.md) i [kontenera](../visual-cpp-samples.md).  
  
 Liczba elementów należy dodać do aplikacji kontenera struktury menu do obsługi OLE. Aby uzyskać więcej informacji o tych zobacz [menu i zasoby: dodatki do kontenera](../mfc/menus-and-resources-container-additions.md).  
  
 Można również obsługuje niektóre z następujących funkcji w aplikacji kontenera:  
  
-   Aktywacja w miejscu podczas edytowania element osadzony.  
  
     Aby uzyskać więcej informacji, zobacz [aktywacji](../mfc/activation-cpp.md).  
  
-   Tworzenie OLE elementów przez przeciąganie i upuszczanie zaznaczenia z aplikacji serwera.  
  
     Aby uzyskać więcej informacji, zobacz [przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md).  
  
-   Łącza do osadzonych obiektów lub kombinacja aplikacje kontenera/serwera.  
  
     Aby uzyskać więcej informacji, zobacz [kontenery: funkcje zaawansowane](../mfc/containers-advanced-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery](../mfc/containers.md)   
 [Kontenery: Elementy klienckie](../mfc/containers-client-items.md)

