---
title: Zawieranie dokumentów aktywnych
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
ms.openlocfilehash: dc13384454c4732d3efbf99def5d05dd4f2d44aa
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776573"
---
# <a name="active-document-containment"></a>Zawieranie dokumentów aktywnych

Zawieranie dokumentów aktywnych jest to technologia, która zawiera jedną klatkę, w której chcesz pracować z dokumentami, zamiast wymuszania wielokrotnego tworzenia i używania wielu klatek aplikacji dla każdego typu dokumentu. Różni się od podstawowych technologii OLE w tym OLE współpracuje z osadzonych obiektów w dokumencie złożonym, w którym może być aktywne tylko jednego elementu zawartości. W kontekście jednej ramce, przy użyciu zawierania dokumentów aktywnych aktywować cały dokument (czyli całej aplikacji, w tym skojarzonego menu, paski narzędzi i tak dalej).

Technologia zawierania dokumentów aktywnych pierwotnie został opracowany pakietu Microsoft Office zaimplementować Office Binder. Jednak ta technologia jest na tyle elastyczna, aby obsługiwać kontenery dokumentów aktywnych niż Office Binder i może obsługiwać serwery dokumentów innych niż aplikacje pakietu Office i zgodny z pakietem Office.

Nosi nazwę aplikacji, która obsługuje dokumenty aktywne [kontener dokumentów aktywnych](../mfc/active-document-containers.md). Przykładami takich kontenery są Microsoft Office Binder ani Microsoft Internet Explorer.

Zawieranie dokumentów aktywnych jest wdrażany jako zestaw rozszerzeń OLE dokumenty technologii złożonego dokumentu OLE. Rozszerzenia są dodatkowe interfejsy, które umożliwiają obiektu możliwego do osadzenia, w miejscu do reprezentowania cały dokument zamiast jednego fragmentu zawartości osadzonej. Podobnie jak w przypadku dokumentów OLE, zawieranie dokumentów aktywnych korzysta z kontenerem, który udostępnia miejsce wyświetlania dokumentów aktywnych i serwerów, które dostarczają interfejs i manipulowania możliwości użytkownika dla samych dokumentach active.

[Serwera aktywnego dokumentu](../mfc/active-document-servers.md) jest aplikacji (takich jak Word, Excel lub PowerPoint), która obsługuje co najmniej jedną klasę aktywnego dokumentu, gdzie każdy obiekt, sama obsługuje interfejsy rozszerzenia, które umożliwiają obiekt, aby ją aktywować na odpowiedniego kontenera.

[Aktywnego dokumentu](../mfc/active-documents.md) (udostępnione z serwera aktywnego dokumentu, takich jak Word lub Excel) jest zasadniczo dobrym przybliżeniem pełnego, konwencjonalnych dokument, który jest osadzony jako obiekt w innym kontenerze aktywnego dokumentu. W przeciwieństwie do osadzonych obiektów active dokumenty mają pełną kontrolę nad nimi strony, a pełna interfejsu aplikacji (przy użyciu wszystkich jego podstawowych poleceń i narzędzi) jest dostępny dla użytkownika do ich edycji.

Aktywny dokument najlepiej zrozumiałe odróżniające ją od standardowego osadzonego obiektu OLE. Po Konwencji OLE osadzony obiekt jest taki, który jest wyświetlany na stronie dokumentu, który jest jego właścicielem i dokumentu jest zarządzana przez kontener OLE. Dane osadzonego obiektu z pozostałej części dokumentu są przechowywane w kontenerze. Osadzone obiekty są jednak ograniczone, kontroluje strony, na którym są wyświetlane.

Użytkownicy aplikacji kontenera dokumentów aktywnych można tworzyć dokumenty aktywne (nazywanych sekcjami Office Binder) przy użyciu swoich ulubionych aplikacji (pod warunkiem te aplikacje są aktywnego dokumentu, włączone), ale użytkownicy mogą zarządzać wynikowych projektu jako pojedyncza jednostka, która może być unikatową nazwę, zapisane, drukowania, i tak dalej. W taki sam sposób użytkownika przeglądarki internetowej można traktować jako jednostki magazynu pojedynczego dokumentu, z możliwością przeglądania dokumenty w tym magazynu z jednej lokalizacji całej sieci, a także systemy pliku lokalnego.

## <a name="sample-programs"></a>Przykładowe programy

- [MFCBIND](../overview/visual-cpp-samples.md) przykładową implementację aplikacji kontenera dokumentów aktywnych.

## <a name="see-also"></a>Zobacz także

[MFC COM](../mfc/mfc-com.md)
