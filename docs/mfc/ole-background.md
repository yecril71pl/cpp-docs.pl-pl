---
title: Podstawy OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: 2501373c2ff5904343a6522e4fb18663f5de3843
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294424"
---
# <a name="ole-background"></a>Podstawy OLE

OLE to mechanizm, który umożliwia użytkownikom tworzenie i edytowanie dokumentów zawierających elementy lub "obiekty" utworzony przez wiele aplikacji.

> [!NOTE]
>  OLE była pierwotnie akronim łączenie i osadzanie obiektów. Jednak go teraz nazywa się OLE. Części nie dotyczą łączenie i osadzanie OLE są teraz częścią technologii Active.

Dokumenty OLE w przeszłości o nazwie dokumentów złożonych, bezproblemowe integrowanie różnych typów danych i składników. Klipów dźwiękowych, arkusze kalkulacyjne i mapy bitowe są typowe przykłady składników w dokumenty OLE. Obsługa OLE w aplikacji umożliwia użytkownikom na używanie dokumentów OLE bez martwienia się o przełączaniu między różnymi aplikacjami; OLE wykonuje przełączenie dla Ciebie.

Jest używany do tworzenia dokumentów złożonych aplikacji kontenera i aplikacji serwera lub składnika aplikacji do tworzenia elementów w obrębie dokumentu kontenera. Każda aplikacja, którą piszesz może być kontenera i/lub serwerem.

OLE zawiera wiele różnych pojęć, współpracujących osiąganiu celu bezproblemowe interakcje między aplikacjami. Te obszary są następujące:

- Łączenie i osadzanie

   Łączenie i osadzanie są dwie metody do przechowywania elementów tworzony w dokumencie OLE, które zostały utworzone w innej aplikacji. Aby uzyskać ogólne informacje na temat różnic między nimi, zobacz artykuł [OLE tła: Łączenie i osadzanie](../mfc/ole-background-linking-and-embedding.md). Aby uzyskać szczegółowe informacje, zobacz artykuły [kontenery](../mfc/containers.md) i [serwerów](../mfc/servers.md).

- Aktywacja w miejscu (edycja wizualna)

   Aktywowanie element osadzony w kontekście kontenerem nosi nazwę aktywacji w miejscu lub edycja wizualna. Interfejs aplikacji kontenera zmieni się na włączenie funkcji aplikacji składnika, który utworzył element osadzony. Połączone elementy są nigdy aktywowany w miejscu, ponieważ rzeczywiste dane dla elementu są przechowywane w oddzielnym pliku, poza kontekstem aplikacji zawierającej łącze. Aby uzyskać więcej informacji o aktywacji w miejscu, zobacz artykuł [aktywacji](../mfc/activation-cpp.md).

   > [!NOTE]
   > Łączenie i osadzanie i aktywacji w miejscu podaj główne funkcje edycja wizualna OLE.

- Automatyzacja usługi Automation umożliwia jedną aplikację do innej aplikacji. Kierowcy aplikacji jest znany jako klient usługi automation i aplikacji są oparte na jest znany jako serwer automatyzacji lub składnik usługi automation. Aby uzyskać więcej informacji na temat automatyzacji, zobacz artykuły [klientów automatyzacji](../mfc/automation-clients.md) i [serwerów automatyzacji](../mfc/automation-servers.md).

   > [!NOTE]
   > Usługa Automation współpracuje w kontekstach technologii zarówno OLE, jak i aktywne. Można zautomatyzować dowolny obiekt oparte na modelu COM.

- Pliki złożone

   Pliki złożone zawierają standardowe formacie, który upraszcza ze strukturą przechowywania dokumentów złożonych aplikacji OLE. W pliku złożonym miejsc wiele funkcji, katalogów i strumieni ma wiele funkcji plików. Ta technologia jest również nazywany strukturalny magazyn. Aby uzyskać więcej informacji na temat plików złożonych, zobacz artykuł [kontenerów: Pliki złożone](../mfc/containers-compound-files.md).

- Transfer danych jednolitego

   Jednolite transferu danych (UDT) to zbiór interfejsów, które dane wysyłanie i odbieranie w sposób standardowy, niezależnie od rzeczywistego metody wybranej do transferu danych. Formularze UDT, których podstawę danych będzie przesyłana przy przeciąganie i upuszczanie. UDT obecnie służy jako podstawa do istniejących Windows transferu danych, takich jak Schowek i dynamiczna wymiana danych (DDE). Aby uzyskać więcej informacji na temat UDT, zobacz artykuł [obiekty danych i źródeł danych (OLE)](../mfc/data-objects-and-data-sources-ole.md).

- Przeciągnij i opuść

   Przeciąganie i upuszczanie jest łatwe w użyciu, bezpośrednie manipulowanie techniki transferu danych między aplikacjami między oknami w aplikacji lub nawet w ramach jednego okna w aplikacji. Transfer danych jest wybrane i przeciągnięte do docelowej lokalizacji. Przeciąganie i upuszczanie opiera się na przesyłanie danych jednolite. Aby uzyskać więcej informacji na temat przeciągania i upuszczania, zobacz artykuł [przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md).

- Model Component Object Model

   Component Object Model (COM) zapewnia infrastrukturę używany, gdy obiekty OLE komunikują się ze sobą. Klasy MFC OLE uprościć COM dla programisty. COM jest częścią technologii aktywnego, ponieważ obiekty COM podstawą technologii zarówno OLE, jak i aktywne. Aby uzyskać więcej informacji na temat modelu COM, zobacz [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md) tematów.

Niektóre z bardziej ważnych tematów OLE są omówione w następujących artykułach:

- [Podstawy OLE: Łączenie i osadzanie](../mfc/ole-background-linking-and-embedding.md)

- [Podstawy OLE: Kontenery i serwery](../mfc/ole-background-containers-and-servers.md)

- [Podstawy OLE: Strategie implementacji](../mfc/ole-background-implementation-strategies.md)

- [Podstawy OLE: Implementacja interfejsu MFC](../mfc/ole-background-mfc-implementation.md)

Nie można odnaleźć w powyższych artykułach ogólne informacje OLE Wyszukaj OLE w bibliotece MSDN.

## <a name="see-also"></a>Zobacz także

[OLE](../mfc/ole-in-mfc.md)
