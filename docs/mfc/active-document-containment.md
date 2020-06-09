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
ms.openlocfilehash: 1c524d6890cd7b86bcae2c40d8c602e7b04e751b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623436"
---
# <a name="active-document-containment"></a>Zawieranie dokumentów aktywnych

Zawieranie dokumentów aktywnych jest technologią, która udostępnia pojedynczą ramkę, w której można korzystać z dokumentów, zamiast wymuszać tworzenie i używanie wielu ramek aplikacji dla każdego typu dokumentu. Różni się od podstawowej technologii OLE w tym, że OLE działa z osadzonymi obiektami w ramach dokumentu złożonego, w którym tylko jedna część zawartości może być aktywna. W przypadku zawierania dokumentów aktywnych można aktywować cały dokument (czyli całą aplikację, w tym skojarzone menu, paski narzędzi itd.) w kontekście pojedynczej ramki.

Technologia zawierania dokumentów aktywnych została pierwotnie opracowana w celu Microsoft Office zaimplementowania programu Office Binder. Jednak technologia ta jest elastyczna, aby obsługiwała kontenery dokumentów aktywnych innego niż program Office Binder i może obsługiwać serwery dokumentów inne niż aplikacje pakietu Office i aplikacji zgodnych z pakietem Office.

Aplikacja, która hostuje aktywne dokumenty, nosi nazwę [kontenera dokumentów aktywnych](active-document-containers.md). Przykładami takich kontenerów są spinacze Microsoft Office lub program Microsoft Internet Explorer.

Zawieranie dokumentów aktywnych jest zaimplementowane jako zestaw rozszerzeń dokumentów OLE, technologii dokumentu złożonego OLE. Rozszerzenia to dodatkowe interfejsy, które umożliwiają osadzenie obiektu w miejscu, aby reprezentować cały dokument zamiast pojedynczego fragmentu osadzonej zawartości. Podobnie jak w przypadku dokumentów OLE, zawiera ona kontener, który udostępnia obszar wyświetlania dla aktywnych dokumentów i serwery, które udostępniają funkcje interfejsu użytkownika i manipulowania dla aktywnych dokumentów.

[Aktywny serwer dokumentów](active-document-servers.md) to aplikacja (np. Word, Excel lub PowerPoint), która obsługuje jedną lub więcej aktywnych klas dokumentów, gdzie każdy obiekt obsługuje interfejsy rozszerzeń, które umożliwiają aktywowanie obiektu w odpowiednim kontenerze.

[Aktywny dokument](active-documents.md) (dostarczany z aktywnego serwera dokumentów, takiego jak Word lub Excel) jest zasadniczo pełnym, konwencjonalnym dokumentem osadzonym jako obiekt w innym kontenerze aktywnego dokumentu. W przeciwieństwie do osadzonych obiektów, aktywne dokumenty mają pełną kontrolę nad swoimi stronami, a pełny interfejs aplikacji (ze wszystkimi podstawowymi poleceniami i narzędziami) jest dostępny dla użytkownika, aby go edytować.

Aktywny dokument jest najlepiej zrozumiały poprzez odróżnienie go od standardowego obiektu OLE osadzonego. Zgodnie z Konwencją OLE osadzony obiekt jest taki, który jest wyświetlany na stronie dokumentu, który jest właścicielem, a dokument jest zarządzany przez kontener OLE. Kontener przechowuje dane osadzonego obiektu w pozostałej części dokumentu. Jednak obiekty osadzone są ograniczone, ponieważ nie kontrolują strony, na której się znajdują.

Użytkownicy aplikacji kontenera dokumentów aktywnych mogą tworzyć aktywne dokumenty (zwane sekcjami w programie Office Binder) przy użyciu ich ulubionych aplikacji (pod warunkiem, że te aplikacje są włączone w aktywnym dokumencie), ale użytkownicy mogą zarządzać wynikowym projektem jako pojedynczą jednostką, która może mieć unikatową nazwę, zapisaną, drukowaną itd. W ten sam sposób użytkownik przeglądarki internetowej może traktować całą sieć, a także lokalne systemy plików, jako jednostkę magazynu o pojedynczym dokumencie, która umożliwia przeglądanie dokumentów w tym magazynie z poziomu pojedynczej lokalizacji.

## <a name="sample-programs"></a>Przykładowe programy

- Przykład [MFCBIND](../overview/visual-cpp-samples.md) ilustruje implementację aplikacji kontenera dokumentów aktywnych.

## <a name="see-also"></a>Zobacz też

[MFC COM](mfc-com.md)
