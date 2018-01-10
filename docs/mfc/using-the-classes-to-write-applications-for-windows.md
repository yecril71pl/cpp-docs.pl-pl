---
title: "Używanie klas do pisania aplikacji dla systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4a8edcabee2f835bd3a3acd0ff3789690764c397
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>Używanie klas do pisania aplikacji dla systemu Windows
Razem z klas w bibliotece Microsoft Foundation Class (MFC) składają się na "Struktura aplikacji," na którym tworzenia aplikacji dla systemu operacyjnego Windows. Na poziomie bardzo ogólne ramach definiuje szkielet aplikacji i dostarcza implementacji standardowy interfejs użytkownika, które mogą być umieszczane na szkielet. Zadanie jako programisty jest wypełnienie w pozostałej części szkielet, które są inne elementy, które są specyficzne dla aplikacji. Utworzyć można uzyskać za pomocą Kreatora aplikacji MFC do tworzenia plików dla aplikacji dokładnego początkowego. Przy użyciu programu Microsoft Visual C++ edytory zasobów zaprojektować wizualnie, elementów interfejsu użytkownika widoku klasy poleceń połączyć te elementy kodu i biblioteki klas logiki specyficzne dla aplikacji.  
  
 W wersji 3.0 lub nowszej programu MFC framework obsługuje programowania dla platformy Win32, w tym Microsoft Windows 95 lub nowszy oraz wersje systemu Windows NT 3.51 lub nowszy. Obsługa MFC Win32 obejmuje wielowątkowości. Użyj wersji 1.5*x* Jeśli trzeba 16-bit — programowanie.  
  
 Tej rodziny artykułów przedstawia ogólne omówienie struktury aplikacji. Eksploruje go także obiekty główne, wchodzące w skład aplikacji i sposób ich tworzenia. Między tematami opisane w następujących artykułach są następujące:  
  
-   [Platformę](../mfc/framework-mfc.md).  
  
-   Dzielenie pracy między platformę i kod, zgodnie z opisem w [opieranie się na strukturze](../mfc/building-on-the-framework.md).  
  
-   [Klasa aplikacji](../mfc/cwinapp-the-application-class.md), który hermetyzuje funkcji na poziomie aplikacji.  
  
-   Jak [szablony dokumentów](../mfc/document-templates-and-the-document-view-creation-process.md) tworzenia i zarządzania dokumentami i ich skojarzonych widoków i okna ramowe.  
  
-   Klasa [CWnd](../mfc/window-objects.md), klasa podstawowa wszystkich okien.  
  
-   [Obiekty graficzne](../mfc/graphic-objects.md), takie jak pióra i pędzle.  
  
 Inne części platformę obejmują:  
  
-   [Obiekty okna: omówienie](../mfc/window-objects.md)  
  
-   [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)  
  
-   [CObject, klasa podstawowa w MFC](../mfc/using-cobject.md)  
  
-   [Architektura dokument/widok](../mfc/document-view-architecture.md)  
  
-   [Okna dialogowe](../mfc/dialog-boxes.md)  
  
-   [Kontrolki](../mfc/controls-mfc.md)  
  
-   [Paski sterowania](../mfc/control-bars.md)  
  
-   [OLE](../mfc/ole-in-mfc.md)  
  
-   [Zarządzanie pamięcią](../mfc/memory-management.md)  
  
     Oprócz daje korzyści w pisania aplikacji dla systemu operacyjnego Windows, MFC również ułatwia do pisania aplikacji, w szczególności używających OLE łączenie i osadzanie technologii. Umożliwia aplikacji OLE visual Edytowanie kontenera i/lub serwerem OLE edycji visual i automatyzacji można dodać, aby inne aplikacje można użyć obiektów z aplikacji lub nawet dysków zdalnie.  
  
-   [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)  
  
     OLE kontroli development kit (CDK) jest teraz w pełni zintegrowana z architekturą. Rodziny ten artykuł zawiera omówienie tworzenia kontrolki ActiveX z MFC. (Formantów ActiveX zostały wcześniej znane jako formantów OLE).  
  
-   [Programowanie bazy danych](../data/data-access-programming-mfc-atl.md)  
  
     MFC dostarcza również dwa zestawy klasy bazy danych, które upraszczają pisania dostęp do danych aplikacji. Używanie klas baz danych ODBC, można nawiązać połączenia z bazami danych za pośrednictwem sterownika otwarte połączenie bazy danych (ODBC), wybrać rekordy z tabel i wyświetlić informacje rekordów w formularza na ekranie. Korzystanie z klas obiektów DAO (Data Access), można pracować z bazami danych za pomocą aparatu bazy danych programu Microsoft Jet lub źródeł danych zewnętrznych (z systemem innym niż Jet), w tym źródeł danych ODBC.  
  
     Ponadto MFC jest w pełni włączone do pisania aplikacji, które używają Unicode i zestawy znaków wielobajtowych (MBCS), zestawy znaków w szczególności znaków dwubajtowych (DBCS).  
  
 Ogólne wskazówki dokumentacji MFC, zobacz [tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

