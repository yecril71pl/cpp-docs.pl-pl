---
title: Podstawy OLE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 262eee08e1bea410fd8e6d12d9209d35877e4a5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355564"
---
# <a name="ole-background"></a>Podstawy OLE
OLE jest mechanizm, który umożliwia użytkownikom tworzenie i edytowanie dokumenty zawierające elementy lub "obiekty" tworzone przez wiele aplikacji.  
  
> [!NOTE]
>  OLE był pierwotnie akronim łączenie i osadzanie obiektów. Jednak jest ona obecnie określana jako OLE. Części nie dotyczą łączenie i osadzanie OLE są teraz częścią aktywnego technologii.  
  
 Dokumenty OLE, w przeszłości o nazwie dokumentów złożonych bezproblemowo integrują się z różnych typów danych lub składników. Dźwięki, arkusze kalkulacyjne i map bitowych są typowe przykłady składników w dokumentów OLE. Obsługa OLE w aplikacji umożliwia użytkownikom używanie dokumenty OLE bez obaw o przełączanie między różnymi aplikacjami; OLE jest przełączanie dla Ciebie.  
  
 Używasz aplikacji kontenera, aby utworzyć dokumenty złożone i serwera aplikacji lub składników aplikacji do tworzenia elementów w dokumencie kontenera. Dowolnej aplikacji, jaki może być kontener i/lub serwerem.  
  
 OLE zawiera wiele różnych pojęcia, które współpracują osiąganiu celu bezproblemowego interakcji między aplikacjami. Te obszary to następujące czynności:  
  
 Łączenie i osadzanie  
 Łączenie i osadzanie są dwie metody przechowywania utworzonych w dokumencie OLE elementów, które zostały utworzone w innej aplikacji. Aby uzyskać ogólne informacje na temat różnic między nimi, zobacz artykuł [tła OLE: łączenie i osadzanie](../mfc/ole-background-linking-and-embedding.md). Aby uzyskać szczegółowe informacje, zobacz artykuły [kontenery](../mfc/containers.md) i [serwerów](../mfc/servers.md).  
  
 Aktywacja w miejscu (edycja wizualna)  
 Aktywowanie element osadzony w kontekście kontenerem nosi nazwę Aktywacja w miejscu lub edycji. Interfejs aplikacji kontenera zmienia się na włączenie funkcji aplikacji składnika, który utworzył element osadzony. Połączone elementy nigdy nie są uaktywnione w miejscu, ponieważ rzeczywistymi danymi na element znajduje się w oddzielnym pliku poza kontekstem aplikacji zawierającej łącze. Aby uzyskać więcej informacji o aktywacji w miejscu, zobacz artykuł [aktywacji](../mfc/activation-cpp.md).  
  
> [!NOTE]
>  Łączenie i osadzanie i aktywacja w miejscu podaj główne funkcje edycja wizualna OLE.  
  
 Automatyzacja  
 Automatyzacja umożliwia jedną aplikację do innej aplikacji. Pobudzenie aplikacji jest znany jako klient automatyzacji i aplikacji prowadzone jest znany jako serwer automatyzacji lub składnik automatyzacji. Aby uzyskać więcej informacji o automatyzacji, zobacz artykuły [klientów automatyzacji](../mfc/automation-clients.md) i [serwery automatyzacji](../mfc/automation-servers.md).  
  
> [!NOTE]
>  Automatyzacja działa w kontekstach Technologia Active i OLE. Można zautomatyzować dowolny obiekt oparte na modelu COM.  
  
 Pliki złożone  
 Pliki złożone zapewniają standardowe formacie, który upraszcza strukturalnych przechowywanie dokumentów złożonych aplikacji OLE. W pliku złożonego miejsc mają wiele funkcji katalogów i strumieni ma wiele funkcji plików. Ta technologia jest również nazywany magazynem strukturalnym. Aby uzyskać więcej informacji na pliki złożone, zobacz artykuł [kontenery: pliki złożone](../mfc/containers-compound-files.md).  
  
 Transfer danych Uniform  
 Jednolite Transfer danych (UDT) to zestaw interfejsów, które umożliwiają danych wysyłanie i odbieranie w sposób standardowy, niezależnie od rzeczywistej metody wybranej do transferu danych. Formularze UDT, których podstawę danych będzie przesyłana przy przeciągnij i upuść. UDT obecnie służy jako podstawa dla istniejących transferu danych systemu Windows, takich jak Schowek i dynamiczna wymiana danych (DDE). Aby uzyskać więcej informacji dotyczących UDT, zobacz artykuł [obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md).  
  
 Przeciągnij i opuść  
 Przeciąganie i upuszczanie jest łatwy w użyciu, bezpośrednie manipulowanie techniki transferu danych między aplikacjami, między systemu windows w aplikacji lub nawet w obrębie jednego okna w aplikacji. Transfer danych jest wybrane i przeciągania do docelowej lokalizacji. Przeciąganie i upuszczanie opiera się na transfer danych uniform. Aby uzyskać więcej informacji na przeciąganie i upuszczanie, zobacz artykuł [przeciągnij i upuść](../mfc/drag-and-drop-ole.md).  
  
 Model Component Object Model  
 Składnik modelu COM (Object) oferuje infrastrukturę, używane podczas obiektów OLE komunikują się ze sobą. Klasy MFC OLE uprościć COM dla programisty. COM wchodzi w skład Technologia Active, ponieważ obiekty COM opierają Technologia Active i OLE. Aby uzyskać więcej informacji na temat modelu COM, zobacz [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md) tematów.  
  
 Niektóre tematy ważniejsze OLE zostały omówione w następujących artykułach:  
  
-   [Podstawy OLE: łączenie i osadzanie](../mfc/ole-background-linking-and-embedding.md)  
  
-   [Podstawy OLE: kontenery i serwery](../mfc/ole-background-containers-and-servers.md)  
  
-   [Podstawy OLE: strategie implementacji](../mfc/ole-background-implementation-strategies.md)  
  
-   [Podstawy OLE: implementacja MFC](../mfc/ole-background-mfc-implementation.md)  
  
 Nie można odnaleźć w powyższych artykułach ogólne informacje OLE wyszukiwanie OLE w witrynie MSDN.  
  
## <a name="see-also"></a>Zobacz też  
 [OLE](../mfc/ole-in-mfc.md)

