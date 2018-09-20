---
title: Kontenery dokumentów aktywnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f2d8dcc81a8e9843ffa84651a6404ba91c9ef3d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394255"
---
# <a name="active-document-containers"></a>Kontenery dokumentów aktywnych

Kontener dokumentów aktywnych, takich jak Microsoft Office Binder lub Internet Explorer umożliwia pracę z kilku dokumentów typy innej aplikacji w ramach jednej ramki (zamiast wymuszania wielokrotnego tworzenia i używania wielu klatek aplikacji dla każdego Typ dokumentu).

Biblioteka MFC zawiera pełną pomoc techniczną dla kontenerów dokumentów aktywnych w `COleDocObjectItem` klasy. Kreator aplikacji MFC można użyć, aby utworzyć kontener aktywnego dokumentu, wybierając **kontener dokumentów aktywnych** pole wyboru na **Obsługa dokumentów złożonych** strony Kreatora aplikacji MFC. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji kontenera dokumentów aktywnych](../mfc/creating-an-active-document-container-application.md).

Aby uzyskać więcej informacji na temat kontenery dokumentów aktywnych zobacz:

- [Wymagania kontenera](#container_requirements)

- [Obiekty lokacji dokumentu](#document_site_objects)

- [Wyświetl obiekty lokacji](#view_site_objects)

- [Obiekt w ramce](#frame_object)

- [Scalanie menu Pomoc](../mfc/help-menu-merging.md)

- [Drukowanie programowe](../mfc/programmatic-printing.md)

- [Obiekty docelowe poleceń](../mfc/message-handling-and-command-targets.md)

##  <a name="container_requirements"></a> Wymagania kontenera

Obsługa aktywnego dokumentu w pojemniku aktywnego dokumentu wymaga więcej niż tylko implementacje interfejsu: wymaga także wiedzę na temat przy użyciu interfejsów jako obiekt. To samo dotyczy rozszerzenia aktywnego dokumentu, gdzie kontenera musi również wie, jak korzystać z tych interfejsów w rozszerzenia w samych dokumentach active.

Kontener dokumentów aktywnych, która integruje się dokumenty aktywne musi:

- Być może obsługiwać magazyn obiektów za pomocą `IPersistStorage` interfejs, oznacza to, musi mieć `IStorage` wystąpienie do każdego aktywnego dokumentu.

- Obsługa podstawowych funkcji osadzania dokumentów OLE, wymagających obiektów "lokacji" (po jednym dla każdej dokumentu lub osadzania) które implementują `IOleClientSite` i `IAdviseSink`.

- Obsługuje aktywacji w miejscu obiekty osadzone lub dokumenty aktywne. Obiekty lokacji kontenera musi implementować `IOleInPlaceSite` i podać kontener ramki `IOleInPlaceFrame`.

- Obsługuje dokumenty aktywne rozszerzeń przez zaimplementowanie `IOleDocumentSite` zapewnienie mechanizmu dla kontenera na komunikowanie się z dokumentu. Opcjonalnie kontenera można implementować interfejsy aktywnego dokumentu `IOleCommandTarget` i `IContinueCallback` do pobrania prostych poleceń, takich jak drukowaniu lub zapisywaniu.

Obiekt w ramce, wyświetlanie obiektów i obiekt kontenera może opcjonalnie zaimplementować `IOleCommandTarget` do obsługi wysyłania niektórych poleceń, zgodnie z opisem w [obiekty docelowe poleceń](../mfc/message-handling-and-command-targets.md). Obiekty widoku i kontenera można również opcjonalnie zaimplementować `IPrint` i `IContinueCallback`, które obsługują drukowanie programowe, zgodnie z opisem w [programowe drukowanie](../mfc/programmatic-printing.md).

Na poniższej ilustracji pokazano koncepcyjny relacje między kontenerem i jego składników (po lewej), a aktywny dokument i widokach (po prawej). Aktywny dokument zarządza magazynem i danymi, a widok wyświetla lub opcjonalnie wyświetla te dane. Interfejsy wytłuszczonym drukiem są wymagane do uczestnictwa w aktywnym dokumencie; pogrubiony i kursywę są opcjonalne. Wszystkie inne interfejsy są wymagane.

![Interfejsy kontenera dokumentów aktywnych](../mfc/media/vc37gj1.gif "vc37gj1")

Dokument, który obsługuje tylko jeden widok można implementować składniki widoku oraz dokument (oznacza to, że ich odpowiednich interfejsów) na jednej klasy konkretnej. Ponadto witryny kontenera, który obsługuje tylko jeden widok w czasie, można połączyć z witryny dokumentów i wyświetlanie witryny w klas konkretnych w jednej lokacji. Obiekt w ramce kontenera, jednak należy w dalszym ciągu odrębne i składników dokumentu kontenera jedynie znajduje się w tym miejscu można nadać pełny obraz architektury; nie występuje według architektury zawierania dokumentów aktywnych.

##  <a name="document_site_objects"></a> Obiekty lokacji dokumentu

W architekturze zawierania dokumentów aktywnych witryny dokumentów jest taka sama jak obiekt lokacji klienta w dokumentach OLE dodając `IOleDocument` interfejsu:

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

Z witryny dokumentów koncepcyjnie to kontener dla jednego lub kilku obiektów "Widok witryna". Każdy obiekt lokacji widok jest skojarzony z widoku poszczególnych obiektów dokumentu zarządzani przez lokację dokumentu. Jeśli kontener obsługuje tylko jeden widok dla każdej witryny dokumentów, można go również zaimplementować witryny dokumentów i wyświetlanie witryny przy użyciu jednej klasy konkretnej.

##  <a name="view_site_objects"></a> Wyświetl obiekty lokacji

Obiekt lokacji Widok kontenera zarządza miejsce wyświetlania w danym widoku dokumentu. Oprócz obsługi standardu `IOleInPlaceSite` zazwyczaj także implementuje interfejs witryny widoku `IContinueCallback` programowe drukowanie kontrolki. (Należy pamiętać, że obiekt widoku nigdy nie wysyła zapytanie o `IContinueCallback` tak naprawdę mogą zostać zaimplementowane na dowolny obiekt życzy sobie kontenera.)

Kontener, który obsługuje wiele widoków, musi mieć możliwość tworzenia widoku wielu obiektów lokacji w ramach witryny dokumentów. Dzięki temu każdy widok przy użyciu oddzielnych Aktywacja i dezaktywacja usługi jak realizowane za pośrednictwem `IOleInPlaceSite`.

##  <a name="frame_object"></a> Obiekt w ramce

Obiekt w ramce kontenera jest w większości przypadków tego samego ramki, w której jest używany do aktywacji w miejscu w dokumentach OLE, to znaczy, ten, który obsługuje negocjacje menu i paska narzędzi. Obiekt widoku ma dostęp do tego obiektu ramki za pośrednictwem `IOleInPlaceSite::GetWindowContext`, która zapewnia również dostęp do obiektu kontenera, reprezentuje dokumentu kontenera (która może obsłużyć negocjacji poziomu okienko narzędzi i wyliczenia zawartego w nim obiektu).

Kontener dokumentów aktywnych można rozszerzyć ramki, dodając `IOleCommandTarget`. Dzięki temu odbierania poleceń, które pochodzą z interfejsu użytkownika aktywnego dokumentu w taki sam sposób, że ten interfejs umożliwia kontener służący do wysyłania tych samych poleceń (takich jak **nowy plik**, **Otwórz**,  **Zapisz jako**, **drukowania**; **Edytuj kopię**, **Wklej**, **Cofnij**i inne) do aktywnego dokumentu. Aby uzyskać więcej informacji, zobacz [obiekty docelowe poleceń](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Zobacz też

[Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)

