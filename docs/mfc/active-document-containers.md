---
title: Kontenery dokumentów aktywnych
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: dc7017a205bedd716e5c87aa23ac96b257af2e16
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626025"
---
# <a name="active-document-containers"></a>Kontenery dokumentów aktywnych

Kontener aktywnego dokumentu, taki jak Microsoft Office Binder lub Internet Explorer, umożliwia współdziałanie z kilkoma dokumentami różnych typów aplikacji w ramach jednej ramki (zamiast wymuszania tworzenia i używania wielu ramek aplikacji dla każdego typu dokumentu).

MFC zapewnia pełną obsługę kontenerów dokumentów aktywnych w `COleDocObjectItem` klasie. Za pomocą Kreatora aplikacji MFC można utworzyć kontener aktywnego dokumentu, zaznaczając pole wyboru **kontener aktywnego dokumentu** na stronie **Obsługa dokumentu złożonego** w Kreatorze aplikacji MFC. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji kontenera dokumentów aktywnych](creating-an-active-document-container-application.md).

Aby uzyskać więcej informacji na temat kontenerów dokumentów aktywnych, zobacz:

- [Wymagania dotyczące kontenera](#container_requirements)

- [Obiekty witryny dokumentów](#document_site_objects)

- [Wyświetlanie obiektów lokacji](#view_site_objects)

- [Frame — obiekt](#frame_object)

- [Scalanie menu Pomoc](help-menu-merging.md)

- [Drukowanie programowe](programmatic-printing.md)

- [Obiekty docelowe poleceń](message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>Wymagania dotyczące kontenera

Obsługa aktywnego dokumentu w kontenerze aktywnego dokumentu oznacza więcej niż tylko implementacje interfejsu: wymaga również znajomości używania interfejsów zawartego obiektu. To samo dotyczy rozszerzeń dokumentów aktywnych, w których kontener musi również wiedzieć, jak korzystać z tych interfejsów rozszerzeń w aktywnych dokumentach.

Kontener aktywnego dokumentu, który integruje aktywne dokumenty, musi:

- Możliwość obsługi magazynu obiektów za pomocą `IPersistStorage` interfejsu, czyli musi zawierać `IStorage` wystąpienie dla każdego aktywnego dokumentu.

- Obsługa podstawowych funkcji osadzania dokumentów OLE, co wymaga "lokacji" (jeden na dokument lub osadzanie), które implementują `IOleClientSite` i `IAdviseSink` .

- Obsługa aktywacji w miejscu obiektów osadzonych lub aktywnych dokumentów. Obiekty lokacji kontenera muszą być zaimplementowane `IOleInPlaceSite` i obiekt ramki kontenera musi dostarczyć `IOleInPlaceFrame` .

- Obsługa rozszerzeń dokumentów aktywnych przez implementację `IOleDocumentSite` programu w celu zapewnienia mechanizmowi odkomunikowania się kontenera z dokumentem. Opcjonalnie kontener może zaimplementować interfejsy aktywnego dokumentu `IOleCommandTarget` i `IContinueCallback` pobrać proste polecenia, takie jak drukowanie lub zapisywanie.

Obiekt Frame, obiekty widoku i obiekt kontenera mogą opcjonalnie zaimplementować `IOleCommandTarget` do obsługi wysyłania niektórych poleceń, zgodnie z opisem w obiekcie [docelowym polecenia](message-handling-and-command-targets.md). Obiekty widoku i kontenera można także opcjonalnie zaimplementować `IPrint` i `IContinueCallback` , aby umożliwić obsługę drukowania programistycznego, jak opisano w temacie [Drukowanie programistyczne](programmatic-printing.md).

Na poniższej ilustracji przedstawiono relacje koncepcyjne między kontenerem i jego składnikami (po lewej) i aktywnym dokumencie i jego widokami (po prawej stronie). Aktywny dokument zarządza magazynem i danymi, a widok wyświetla lub opcjonalnie drukuje dane. Interfejsy pogrubione są wymagane do współdziałania z dokumentem aktywnym. te pogrubione i kursywy są opcjonalne. Wszystkie inne interfejsy są wymagane.

![Interfejsy kontenera dokumentów aktywnych](../mfc/media/vc37gj1.gif "Interfejsy kontenera dokumentów aktywnych")

Dokument obsługujący tylko jeden widok może zaimplementować zarówno składniki widoku, jak i dokumentu (to oznacza, że odpowiadające im interfejsy) w pojedynczej klasie konkretnej. Ponadto lokacja kontenera, która obsługuje tylko jeden widok jednocześnie, może łączyć lokację dokumentu i widok z jedną klasą konkretnej lokacji. Obiekt ramki kontenera, jednak musi pozostać odrębny, a składnik dokumentu kontenera jest zawarty tutaj tylko w celu uzyskania pełnego obrazu architektury; nie ma to wpływ na architekturę zawierania dokumentów aktywnych.

## <a name="document-site-objects"></a><a name="document_site_objects"></a>Obiekty witryny dokumentów

W przypadku architektury zawierania aktywnego dokumentu witryna dokumentu jest taka sama jak obiekt lokacji klienta w dokumentach OLE z dodaniem `IOleDocument` interfejsu:

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

Witryna dokumentu jest koncepcyjnie kontenerem dla co najmniej jednego obiektu "View Site". Każdy obiekt witryny widoku jest skojarzony z pojedynczymi obiektami widoku dokumentu zarządzanego przez witrynę dokumentu. Jeśli kontener obsługuje tylko jeden widok na każdą witrynę dokumentu, można zaimplementować witrynę dokumentu i witrynę widoku przy użyciu pojedynczej konkretnej klasy.

## <a name="view-site-objects"></a><a name="view_site_objects"></a>Wyświetlanie obiektów lokacji

Obiekt witryny widoku kontenera zarządza obszarem wyświetlania dla określonego widoku dokumentu. Oprócz obsługi standardowego `IOleInPlaceSite` interfejsu, witryna widoku również zazwyczaj implementuje program `IContinueCallback` programistyczny kontroli drukowania. (Należy zauważyć, że obiekt widoku nigdy nie wykonuje zapytania `IContinueCallback` , aby można go było zaimplementować na dowolnym obiekcie, do którego się odniesie kontener).

Kontener obsługujący wiele widoków musi mieć możliwość tworzenia wielu obiektów widoku w obrębie witryny dokumentów. Zapewnia to każdy widok z oddzielnymi usługami aktywacji i dezaktywacji zgodnie z oczekiwaniami `IOleInPlaceSite` .

## <a name="frame-object"></a><a name="frame_object"></a>Frame — obiekt

Obiekt ramki kontenera to, w większości, ta sama ramka, która jest używana do aktywacji w miejscu w dokumentach OLE, czyli, która obsługuje negocjowanie menu i paska narzędzi. Obiekt widoku ma dostęp do tego obiektu ramki przez `IOleInPlaceSite::GetWindowContext` , który również zapewnia dostęp do obiektu kontenera reprezentującego dokument kontenera (który może obsłużyć negocjację paska narzędzi na poziomie okienka i Wyliczenie zawartego obiektu).

Kontener aktywnego dokumentu może rozszerzyć ramkę przez dodanie `IOleCommandTarget` . Dzięki temu można odbierać polecenia pochodzące z interfejsu użytkownika aktywnego dokumentu w taki sam sposób, w jaki ten interfejs może zezwalać kontenerowi na wysyłanie tych samych poleceń (takich jak **plik New**, **Open**, **Save as**, **Print**; **Edytuj kopię**, **Wklej**, **Cofnij**i inne) do aktywnego dokumentu. Aby uzyskać więcej informacji, zobacz [cele poleceń](message-handling-and-command-targets.md).

## <a name="see-also"></a>Zobacz też

[Zawieranie dokumentów aktywnych](active-document-containment.md)
