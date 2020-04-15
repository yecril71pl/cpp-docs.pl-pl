---
title: Kontenery dokumentów aktywnych
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: e2005ffed592fa1de278e0f6339d94687a20fd06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377384"
---
# <a name="active-document-containers"></a>Kontenery dokumentów aktywnych

Aktywny kontener dokumentów, taki jak Microsoft Office Binder lub Internet Explorer, umożliwia pracę z kilkoma dokumentami różnych typów aplikacji w ramach jednej ramki (zamiast wymuszać tworzenie i używanie wielu ramek aplikacji dla każdego typu dokumentu).

MFC zapewnia pełną obsługę kontenerów `COleDocObjectItem` aktywnych dokumentów w klasie. Za pomocą Kreatora aplikacji MFC można utworzyć aktywny kontener dokumentów, zaznaczając pole wyboru **Aktywny kontener dokumentów** na stronie Obsługa dokumentów **złożonych** Kreatora aplikacji MFC. Aby uzyskać więcej informacji, zobacz [Tworzenie aktywnej aplikacji kontenera dokumentów](../mfc/creating-an-active-document-container-application.md).

Aby uzyskać więcej informacji na temat kontenerów aktywnych dokumentów, zobacz:

- [Wymagania dotyczące kontenerów](#container_requirements)

- [Obiekty witryny dokumentu](#document_site_objects)

- [Wyświetlanie obiektów witryny](#view_site_objects)

- [Obiekt ramki](#frame_object)

- [Scalanie menu Pomoc](../mfc/help-menu-merging.md)

- [Drukowanie programowe](../mfc/programmatic-printing.md)

- [Obiekty docelowe poleceń](../mfc/message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>Wymagania dotyczące kontenerów

Obsługa aktywnych dokumentów w kontenerze aktywnego dokumentu oznacza więcej niż tylko implementacje interfejsu: wymaga również wiedzy na temat korzystania z interfejsów obiektu zawartego. To samo dotyczy aktywnych rozszerzeń dokumentów, gdzie kontener musi również wiedzieć, jak używać tych interfejsów rozszerzenia w samych aktywnych dokumentach.

Aktywny kontener dokumentów, który integruje aktywne dokumenty, musi:

- Być w stanie obsługi `IPersistStorage` magazynu obiektów za pośrednictwem interfejsu, oznacza to, że musi dostarczyć wystąpienie `IStorage` do każdego aktywnego dokumentu.

- Obsługa podstawowych funkcji osadzania dokumentów OLE, co wymaga obiektów "lokacji" `IOleClientSite` `IAdviseSink`(po jednym na dokument lub osadzanie), które implementują i .

- Obsługa aktywacji w miejscu osadzonych obiektów lub aktywnych dokumentów. Obiekty lokacji kontenera `IOleInPlaceSite` muszą zostać zaimplementować, a obiekt ramki kontenera musi zawierać . `IOleInPlaceFrame`

- Obsługa rozszerzenia aktywnych dokumentów przez `IOleDocumentSite` wdrożenie w celu zapewnienia mechanizmu kontenera, aby porozmawiać z dokumentem. Opcjonalnie kontener może zaimplementować `IOleCommandTarget` `IContinueCallback` aktywne interfejsy dokumentu i odebrać proste polecenia, takie jak drukowanie lub zapisywanie.

Obiekt ramki, obiekty widoku i obiekt kontenera `IOleCommandTarget` mogą opcjonalnie zaimplementować w celu obsługi wysyłania niektórych poleceń, jak omówiono w [artykule Cele polecenia](../mfc/message-handling-and-command-targets.md). Obiekty widoku i kontenera `IPrint` mogą `IContinueCallback`również opcjonalnie implementować i obsługiwać drukowanie programowe, jak omówiono w [artykule Drukowanie programowe.](../mfc/programmatic-printing.md)

Na poniższej ilustracji przedstawiono relacje koncepcyjne między kontenerem i jego składnikami (po lewej) i aktywnym dokumentem i jego widokami (po prawej). Aktywny dokument zarządza magazynem i danymi, a w widoku są wyświetlane lub opcjonalnie drukowane te dane. Interfejsy pogrubione są interfejsy wymagane do aktywnego udziału w dokumencie; te pogrubione i kursywą są opcjonalne. Wszystkie inne interfejsy są wymagane.

![Aktywne interfejsy kontenerów dokumentów](../mfc/media/vc37gj1.gif "Aktywne interfejsy kontenerów dokumentów")

Dokument, który obsługuje tylko jeden widok można zaimplementować zarówno widok i składniki dokumentu (czyli ich odpowiednich interfejsów) w jednej konkretnej klasy. Ponadto lokacja kontenera, która obsługuje tylko jeden widok naraz, może łączyć witrynę dokumentu i witrynę widoku w jedną konkretną klasę lokacji. Obiekt ramki kontenera musi jednak pozostać odrębny, a składnik dokumentu kontenera jest tylko uwzględniony w tym miejscu, aby uzyskać pełny obraz architektury; nie ma na nią wpływu architektura zamknięcia aktywnego dokumentu.

## <a name="document-site-objects"></a><a name="document_site_objects"></a>Obiekty witryny dokumentu

W architekturze bezpieczeństwa aktywnego dokumentu witryna dokumentu jest taka sama jak obiekt `IOleDocument` lokacji klienta w dokumentach OLE z dodatkiem interfejsu:

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

Witryna dokumentu jest koncepcyjnie kontenerem dla jednego lub więcej obiektów "view site". Każdy obiekt witryny widoku jest skojarzony z poszczególnymi obiektami widoku dokumentu zarządzanego przez witrynę dokumentu. Jeśli kontener obsługuje tylko jeden widok na witrynę dokumentu, można zaimplementować witrynę dokumentu i witrynę widoku z jedną klasą konkretów.

## <a name="view-site-objects"></a><a name="view_site_objects"></a>Wyświetlanie obiektów witryny

Obiekt witryny widoku kontenera zarządza przestrzenią wyświetlania dla określonego widoku dokumentu. Oprócz obsługi standardowego `IOleInPlaceSite` interfejsu, witryna widoku jest `IContinueCallback` również ogólnie implementuje dla sterowania drukowaniem programowym. (Należy zauważyć, że obiekt `IContinueCallback` widoku nigdy nie wysyła zapytań, więc faktycznie można go zaimplementować na dowolnym obiekcie, którego dotyczy kontener).

Kontener obsługujący wiele widoków musi mieć możliwość tworzenia wielu obiektów witryny widoku w witrynie dokumentu. Zapewnia to każdemu widokowi oddzielne usługi aktywacji i dezaktywacji, które są świadczone za pośrednictwem . `IOleInPlaceSite`

## <a name="frame-object"></a><a name="frame_object"></a>Obiekt ramki

Obiekt ramki kontenera jest w przeważającej części tą samą ramką, która jest używana do aktywacji w miejscu w dokumentach OLE, czyli tej, która obsługuje negocjacje menu i paska narzędzi. Obiekt widoku ma dostęp do `IOleInPlaceSite::GetWindowContext`tego obiektu ramki za pośrednictwem , który zapewnia również dostęp do obiektu kontenera reprezentującego dokument kontenera (który może obsługiwać negocjacji na poziomie paska narzędzi i zawarte wyliczenie obiektu).

Aktywny kontener dokumentu może rozszerzyć ramkę, dodając `IOleCommandTarget`program . Dzięki temu może odbierać polecenia pochodzące z interfejsu użytkownika aktywnego dokumentu w taki sam sposób, w jaki ten interfejs może zezwolić kontenerowi na wysyłanie tych samych poleceń (takich jak **File New**, **Open**, **Save As**, **Print**; **Edytuj kopię,** **wklej,** **Cofnij**i inne) do aktywnego dokumentu. Aby uzyskać więcej informacji, zobacz [Cele poleceń](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Zobacz też

[Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)
