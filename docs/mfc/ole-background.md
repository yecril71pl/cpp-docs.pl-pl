---
title: Podstawy OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: f7d65f48c1af678f6626ba7d315ceb735d3e960a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364521"
---
# <a name="ole-background"></a>Podstawy OLE

OLE to mechanizm, który umożliwia użytkownikom tworzenie i edytowanie dokumentów zawierających elementy lub "obiekty" utworzone przez wiele aplikacji.

> [!NOTE]
> OLE był pierwotnie skrótem od łączenia i osadzania obiektów. Jednak teraz jest określany jako OLE. Części OLE niezwiązanych z łączenia i osadzania są teraz częścią technologii Active.

Dokumenty OLE, historycznie nazywane dokumentami złożonymi, bezproblemowo integrują różne typy danych lub składniki. Klipy dźwiękowe, arkusze kalkulacyjne i mapy bitowe są typowymi przykładami składników znalezionych w dokumentach OLE. Obsługa ole w aplikacji umożliwia użytkownikom korzystanie z dokumentów OLE bez martwienia się o przełączanie między różnymi aplikacjami; OLE wykonuje przełączanie za Ciebie.

Aplikacja kontenera służy do tworzenia dokumentów złożonych i aplikacji serwera lub aplikacji składnika do tworzenia elementów w dokumencie kontenera. Każda aplikacja, którą piszesz, może być kontenerem, serwerem lub obiema.

OLE zawiera wiele różnych pojęć, które wszystkie działają w kierunku celu bezproblemowej interakcji między aplikacjami. Obszary te są następujące:

- łączenie i osadzanie

   Łączenie i osadzanie to dwie metody przechowywania elementów utworzonych wewnątrz dokumentu OLE, które zostały utworzone w innej aplikacji. Aby uzyskać ogólne informacje na temat różnic między nimi, zobacz artykuł [OLE Tło: Łączenie i osadzanie](../mfc/ole-background-linking-and-embedding.md). Aby uzyskać bardziej szczegółowe informacje, zobacz artykuły [Kontenery](../mfc/containers.md) i [Serwery](../mfc/servers.md).

- Aktywacja w miejscu (edycja wizualna)

   Aktywowanie elementu osadzonego w kontekście dokumentu kontenera jest nazywane aktywacją w miejscu lub edycją wizualną. Interfejs aplikacji kontenera zmienia się, aby uwzględnić funkcje aplikacji składnika, który utworzył element osadzony. Połączone elementy nigdy nie są aktywowane w miejscu, ponieważ rzeczywiste dane dla elementu znajduje się w oddzielnym pliku, z kontekstu aplikacji zawierającej łącze. Aby uzyskać więcej informacji na temat aktywacji w miejscu, zobacz artykuł [Aktywacja](../mfc/activation-cpp.md).

   > [!NOTE]
   > Łączenie i osadzanie oraz aktywacja w miejscu zapewniają główne cechy edycji wizualnej OLE.

- Automatyzacja automatyzacji umożliwia jednej aplikacji do kierowania inną aplikacją. Aplikacja do prowadzenia pojazdów jest znana jako klient automatyzacji, a kierowana aplikacja jest znana jako serwer automatyzacji lub składnik automatyzacji. Aby uzyskać więcej informacji na temat automatyzacji, zobacz artykuły [Klienci automatyzacji](../mfc/automation-clients.md) i [serwery automatyzacji](../mfc/automation-servers.md).

   > [!NOTE]
   > Automatyzacja działa zarówno w kontekście technologii OLE, jak i Active. Można zautomatyzować dowolny obiekt na podstawie com.

- pliki złożone

   Pliki złożone zapewniają standardowy format pliku, który upraszcza ustrukturyzowane przechowywanie złożonych dokumentów dla aplikacji OLE. W pliku złożonym magazyny mają wiele funkcji katalogów, a strumienie mają wiele funkcji plików. Technologia ta jest również nazywana magazynowaniem strukturalnym. Aby uzyskać więcej informacji na temat plików złożonych, zobacz artykuł [Kontenery: Pliki złożone](../mfc/containers-compound-files.md).

- Jednolity transfer danych

   Uniform Data Transfer (UDT) to zestaw interfejsów, które umożliwiają przesyłanie i odbieranie danych w standardowy sposób, niezależnie od rzeczywistej metody wybranej do przesyłania danych. UDT stanowi podstawę do przesyłania danych przez przeciąganie i upuszczanie. UDT służy teraz jako podstawa dla istniejącego transferu danych systemu Windows, takiego jak Schowek i dynamiczna wymiana danych (DDE). Aby uzyskać więcej informacji na temat UDT, zobacz artykuł [Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md).

- Przeciągnij i opuść

   Przeciąganie i upuszczanie jest łatwą w użyciu techniką bezpośredniej manipulacji do przesyłania danych między aplikacjami, między oknami w aplikacji lub nawet w jednym oknie w aplikacji. Dane, które mają zostać przesłane, zostaną wybrane i przeciągnięte do żądanego miejsca docelowego. Przeciąganie i upuszczanie opiera się na jednolitym transferze danych. Aby uzyskać więcej informacji na temat przeciągania i upuszczania, zobacz artykuł [Przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md).

- Model obiektu komponentu

   Model obiektu komponentu (COM) zapewnia infrastrukturę używaną, gdy obiekty OLE komunikują się ze sobą. Klasy OLE MFC upraszczają com dla programisty. COM jest częścią technologii Active, ponieważ obiekty COM są podstawą zarówno technologii OLE, jak i Active. Aby uzyskać więcej informacji na temat usługi COM, zobacz tematy [aktywnej biblioteki szablonów (ATL).](../atl/active-template-library-atl-concepts.md)

Niektóre z ważniejszych tematów OLE są omówione w następujących artykułach:

- [Podstawy OLE: łączenie i osadzanie](../mfc/ole-background-linking-and-embedding.md)

- [Podstawy OLE: kontenery i serwery](../mfc/ole-background-containers-and-servers.md)

- [Podstawy OLE: strategie implementacji](../mfc/ole-background-implementation-strategies.md)

- [Podstawy OLE: implementacja MFC](../mfc/ole-background-mfc-implementation.md)

Aby uzyskać ogólne informacje OLE nie znaleziono w powyższych artykułach, wyszukaj OLE w MSDN.

## <a name="see-also"></a>Zobacz też

[OLE](../mfc/ole-in-mfc.md)
