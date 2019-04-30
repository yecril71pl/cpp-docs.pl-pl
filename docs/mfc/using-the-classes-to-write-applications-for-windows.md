---
title: Używanie klas do pisania aplikacji dla systemu Windows
ms.date: 11/04/2016
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
ms.openlocfilehash: c8b3d7061c0ef06063d9c6993f24d23fc2e1f92e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411477"
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>Używanie klas do pisania aplikacji dla systemu Windows

Razem wzięte klas w bibliotece Microsoft Foundation Class (MFC) tworzą "strukturę aplikacji," na którym tworzysz aplikację dla systemu operacyjnego Windows. Na poziomie bardzo ogólne struktura definiuje szkielet aplikacji i dostarcza implementacji standardowego interfejsu użytkownika, które mogą być umieszczane na szkielet. Zadanie jako programisty jest wypełnienie w pozostałej części szkielet, służą do powyższych czynności, które są specyficzne dla aplikacji. Za pomocą Kreatora aplikacji MFC do tworzenia plików dla aplikacji dokładnego modułu uruchamiającego, możesz uzyskać łatwiej rozpocząć pracę. Microsoft Visual C++ edytory zasobów wizualnie projektować elementów interfejsu użytkownika widoku klasy polecenia, aby nawiązać połączenie z tych elementów kodu i biblioteki klas umożliwia zaimplementować logikę specyficzne dla aplikacji.

W wersji 3.0 i nowszych programu MFC framework obsługuje programowania na platformach Win32, łącznie z systemu Microsoft Windows 95 lub nowszy i wersji systemu Windows NT 3.51 lub nowszej. Obsługa MFC Win32 obejmuje wielowątkowości. Użyj wersji 1.5*x* Jeśli musisz wykonać programowania 16-bitowych.

Tej rodziny artykuły przedstawia ogólne omówienie struktury aplikacji. On również odkrywa główne obiekty, które tworzą aplikację i jak są tworzone. Wśród omówione w tych artykułach są następujące:

- [Struktura](../mfc/framework-mfc.md).

- Podział pracy między, a kod, zgodnie z opisem w ramach [opieranie się na strukturze](../mfc/building-on-the-framework.md).

- [Klasa aplikacji](../mfc/cwinapp-the-application-class.md), która hermetyzuje funkcjonalność na poziomie aplikacji.

- Jak [szablony dokumentów](../mfc/document-templates-and-the-document-view-creation-process.md) tworzenia i zarządzania dokumentami i ich skojarzone widoków i okna ramowe.

- Klasa [CWnd](../mfc/window-objects.md), klasa bazowa wszystkich okien.

- [Obiekty graficzne](../mfc/graphic-objects.md), takich jak pióra i pędzle.

Inne części ramach obejmują:

- [Obiekty okna: omówienie](../mfc/window-objects.md)

- [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)

- [CObject, klasa bazowa w MFC](../mfc/using-cobject.md)

- [Architektura dokument/widok](../mfc/document-view-architecture.md)

- [Okna dialogowe](../mfc/dialog-boxes.md)

- [Kontrolki](../mfc/controls-mfc.md)

- [Paski sterowania](../mfc/control-bars.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Zarządzanie pamięcią](../mfc/memory-management.md)

   Oprócz zapewnia korzyści w pisaniu aplikacji dla systemu operacyjnego Windows, MFC sprawia, że jej znacznie łatwiejsze do pisania aplikacji, które w szczególności użyj OLE, łączenie i osadzanie technologii. Możesz przekształcić aplikacji OLE edytowania kontenera i/lub serwerem OLE edycji visual obrazu, i tak, aby inne aplikacje mogą używać obiektów z aplikacji lub nawet dysku zdalnie, można dodać usługi Automation.

- [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

   Kontrolki OLE deweloperski (CDK) jest teraz w pełni zintegrowana z architekturą. Tej rodziny artykułu dostarcza przegląd Tworzenie formantów ActiveX z MFC. (Formantów ActiveX były wcześniej znane jako formantów OLE).

- [Programowanie bazy danych](../data/data-access-programming-mfc-atl.md)

   MFC dostarcza również dwa zestawy klasy bazy danych, które upraszczają zapis dostęp do danych aplikacji. Używanie klas baz danych ODBC, może nawiązać połączenie z bazami danych za pośrednictwem sterownika Open Database Connectivity (ODBC), wybierz rekordy z tabel i wyświetlania rekordów informacji w formularza na ekranie. Przy użyciu klas dostępu do obiektu DAO (Data), można pracować z bazami danych za pomocą aparatu bazy danych Microsoft Jet lub źródeł danych zewnętrznych (inne niż Jet), w tym źródeł danych ODBC.

   Ponadto pełnym włączeniem MFC do tworzenia aplikacji, które używają Unicode i (znaków MBCS) zestawów znaków wielobajtowych, zestawy znaków specjalnie znaków dwubajtowych (DBCS).

Ogólne wskazówki dokumentacji MFC, zobacz [tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md).

## <a name="see-also"></a>Zobacz także

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
