---
title: Podstawy OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: 96ece9a2a5be6ea29c95e17e81f6ce4adbfd4c0b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624167"
---
# <a name="ole-background"></a>Podstawy OLE

OLE to mechanizm, który umożliwia użytkownikom tworzenie i edytowanie dokumentów zawierających elementy lub "obiekty" utworzone przez wiele aplikacji.

> [!NOTE]
> Obiekt OLE był pierwotnie akronimem do łączenia i osadzania obiektów. Jest to jednak nazywane OLE. Elementy OLE, które nie są związane z łączeniem i osadzaniem, są teraz częścią aktywnej technologii.

Dokumenty OLE, historycznie nazywane dokumentami złożonymi, bezproblemowo integrują różne typy danych lub składniki. Klipy dźwiękowe, arkusze kalkulacyjne i mapy bitowe są typowymi przykładami składników znajdujących się w dokumentach OLE. Obsługa OLE w aplikacji umożliwia użytkownikom korzystanie z dokumentów OLE bez konieczności przełączania się między różnymi aplikacjami. Mechanizm OLE wykonuje przełączenie.

Aplikacja kontenera służy do tworzenia dokumentów złożonych i aplikacji serwera lub aplikacji składników w celu utworzenia elementów w ramach dokumentu kontenera. Każda zapisana aplikacja może być kontenerem, serwerem lub jednocześnie.

Technologia OLE obejmuje wiele różnych koncepcji, które działają w kierunku bezproblemowego oddziaływania między aplikacjami. Te obszary obejmują następujące elementy:

- łączenie i osadzanie

   Łączenie i osadzanie to dwie metody przechowywania elementów utworzonych wewnątrz dokumentu OLE, które zostały utworzone w innej aplikacji. Aby uzyskać ogólne informacje o różnicach między tymi dwoma, zobacz artykuł [OLE: łączenie i osadzanie](ole-background-linking-and-embedding.md). Aby uzyskać szczegółowe informacje, zobacz artykuły [kontenery](containers.md) i [serwery](servers.md).

- Aktywacja w miejscu (edytowanie wizualizacji)

   Aktywowanie osadzonego elementu w kontekście dokumentu kontenera jest nazywane aktywacją w miejscu lub edycją wizualizacji. Interfejs aplikacji kontenera zmienia się w celu uwzględnienia funkcji aplikacji składnika, która utworzyła element osadzony. Połączone elementy nigdy nie są aktywowane, ponieważ rzeczywiste dane dla tego elementu są zawarte w osobnym pliku, z kontekstu aplikacji zawierającej link. Aby uzyskać więcej informacji na temat aktywacji w miejscu, zobacz [Aktywacja](activation-cpp.md)artykułu.

   > [!NOTE]
   > Łączenie i osadzanie oraz Aktywacja w miejscu udostępnia główne funkcje edycji wizualizacji OLE.

- Automatyzacja automatyzacji umożliwia jednej aplikacji dyskowej innej aplikacji. Aplikacja do kierowania jest znana jako klient usługi Automation, a oparta na niej aplikacja jest znana jako serwer automatyzacji lub składnik automatyzacji. Aby uzyskać więcej informacji na temat automatyzacji, zobacz artykuły [klienci usługi Automation](automation-clients.md) i [serwery automatyzacji](automation-servers.md).

   > [!NOTE]
   > Automatyzacja działa zarówno w kontekście OLE, jak i aktywnych. Można zautomatyzować każdy obiekt na podstawie modelu COM.

- pliki złożone

   Pliki złożone zapewniają standardowy format plików, który upraszcza przechowywanie uporządkowanych dokumentów dla aplikacji OLE. W pliku złożonym magazyny mają wiele funkcji katalogów i strumieni ma wiele funkcji plików. Ta technologia jest również nazywana magazynem strukturalnym. Aby uzyskać więcej informacji na temat plików złożonych, zobacz [kontenery artykułów: pliki złożone](containers-compound-files.md).

- Uniform Data Transfer

   Uniform Data Transfer (UDT) to zestaw interfejsów, które umożliwiają wysyłanie i odbieranie danych w standardowy sposób, niezależnie od rzeczywistej metody transferu danych. UDT stanowi podstawę do transferowania danych przez przeciąganie i upuszczanie. Typ UDT służy teraz jako podstawa istniejącego transferu danych systemu Windows, takiego jak schowek i dynamiczna wymiana danych (DDE). Aby uzyskać więcej informacji na temat UDT, zapoznaj się z tematem [obiekty danych artykułu i źródła danych (OLE)](data-objects-and-data-sources-ole.md).

- Przeciągnij i opuść

   Przeciąganie i upuszczanie jest łatwą w użyciu techniką bezpośredniego manipulowania do przenoszenia danych między aplikacjami, między oknami w aplikacji, a nawet w jednym oknie w aplikacji. Dane, które mają być transferowane, są wybierane i przeciągane do żądanego miejsca docelowego. Przeciąganie i upuszczanie odbywa się na podstawie jednolitego transferu danych. Aby uzyskać więcej informacji na temat przeciągania i upuszczania, zobacz artykuł [Przeciąganie i upuszczanie](drag-and-drop-ole.md).

- Component Object Model

   Component Object Model (COM) zapewnia infrastrukturę używaną, gdy obiekty OLE komunikują się ze sobą. Klasy OLE MFC upraszczają model COM dla programisty. COM jest częścią aktywnej technologii, ponieważ obiekty COM podstawą zarówno OLE, jak i Technologia Active. Aby uzyskać więcej informacji na temat modelu COM, zobacz tematy [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md) .

Niektóre z ważniejszych tematów OLE zostały omówione w następujących artykułach:

- [Podstawy OLE: łączenie i osadzanie](ole-background-linking-and-embedding.md)

- [Podstawy OLE: kontenery i serwery](ole-background-containers-and-servers.md)

- [Podstawy OLE: strategie implementacji](ole-background-implementation-strategies.md)

- [Podstawy OLE: implementacja MFC](ole-background-mfc-implementation.md)

Ogólne informacje o technologii OLE, które nie zostały znalezione w powyższych artykułach, można znaleźć w witrynie MSDN.

## <a name="see-also"></a>Zobacz też

[OLE](ole-in-mfc.md)
