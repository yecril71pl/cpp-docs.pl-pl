---
title: Zawieranie kontrolek ALT — Często zadawane pytania
ms.date: 11/04/2016
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
ms.openlocfilehash: 36ff3381447b46b28908522d65be9f34fe23addf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317402"
---
# <a name="atl-control-containment-faq"></a>Zawieranie kontrolek ALT — Często zadawane pytania

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>Które klasy ATL umożliwiają zawieranie kontrolek ActiveX?

Kod hostingu sterowania ATL nie wymaga używania żadnych klas ATL; możesz po prostu utworzyć okno **"AtlAxWin80"** i w razie potrzeby użyć interfejsu API hostingu kontrolnego (aby uzyskać więcej informacji, zobacz **Co to jest API hostingu ATL Control.** Jednak następujące klasy ułatwiają korzystanie z funkcji hermetyzacji.

|Klasa|Opis|
|-----------|-----------------|
|[CAxWindow ( CAxWindow )](../atl/reference/caxwindow-class.md)|Zawija okno **"AtlAxWin80",** zapewniając metody tworzenia okna, tworzenia formantu i/lub dołączania formantu do okna i pobierania wskaźników interfejsu na obiekcie hosta.|
|[CAxWindow2T (polski)](../atl/reference/caxwindow2t-class.md)|Zawija okno **"AtlAxWinLic80",** udostępnia metody tworzenia okna, tworzenia formantu i/lub dołączania licencjonowanego formantu do okna i pobierania wskaźników interfejsu na obiekcie hosta.|
|[Sterowanie CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Działa jako klasa podstawowa dla klas kontroli ActiveX na podstawie zasobu okna dialogowego. Takie formanty mogą zawierać inne formanty ActiveX.|
|[Caxdialogimpl](../atl/reference/caxdialogimpl-class.md)|Działa jako klasa podstawowa dla klas dialogowych na podstawie zasobu okna dialogowego. Takie okna dialogowe mogą zawierać formanty ActiveX.|
|[Cwindow](../atl/reference/cwindow-class.md)|Udostępnia metodę [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), która zwróci wskaźnik interfejsu na formancie, biorąc pod uwagę identyfikator okna hosta. Ponadto otoki interfejsu API systemu `CWindow` Windows udostępniane przez ogólnie ułatwić zarządzanie oknami.|

## <a name="what-is-the-atl-control-hosting-api"></a>Co to jest interfejs API hostingu kontrolek ATL?

Interfejs API hostingu sterowania ATL to zestaw funkcji, który umożliwia każdemu okno działanie jako kontener formantu ActiveX. Te funkcje mogą być statycznie lub dynamicznie połączone z projektem, ponieważ są one dostępne jako kod źródłowy i udostępniane przez plik ATL90.dll. Funkcje hostingu sterowania są wymienione w poniższej tabeli.

|Funkcja|Opis|
|--------------|-----------------|
|[AtlAxAttachControl (AtlAxAttachControl)](reference/composite-control-global-functions.md#atlaxattachcontrol)|Tworzy obiekt hosta, łączy go z dostarczonym oknem, a następnie dołącza istniejący formant.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Tworzy obiekt hosta, łączy go z dostarczonym oknem, a następnie ładuje formant.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i obsługuje w określonym oknie, podobnie jak [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Tworzy obiekt hosta, łączy go z dostarczonym oknem, a następnie ładuje formant (umożliwia również ustawienie pochłaniaczy zdarzeń).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Tworzy licencjonowany formant ActiveX, inicjuje go i obsługuje w określonym oknie, podobnie jak [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Tworzy niemodowe okno dialogowe z zasobu okna dialogowego i zwraca uchwyt okna.|
|[Skrzynka z promieniami 2010](reference/composite-control-global-functions.md#atlaxdialogbox)|Tworzy modalne okno dialogowe z zasobu okna dialogowego.|
|[Kontrola AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Zwraca wskaźnik interfejsu **IUnknown** formantu hostowanego w oknie.|
|[AtlAxGetHost (AtlAxGetHost)](reference/composite-control-global-functions.md#atlaxgethost)|Zwraca wskaźnik interfejsu **IUnknown** obiektu hosta połączonego z oknem.|
|[AtlAxWinInit (AtlAxWinInit)](reference/composite-control-global-functions.md#atlaxwininit)|Inicjuje kod hostingu formantu.|
|[AtlAxWinTerm (własnoręcznisze)](reference/composite-control-global-functions.md#atlaxwinterm)|Uninitializes kodu hostingu formantu.|

Parametry `HWND` w pierwszych trzech funkcji musi być istniejące okno (prawie) dowolnego typu. Jeśli wywołasz dowolną z tych trzech funkcji jawnie (zazwyczaj nie trzeba), nie należy przekazywać dojście do okna, które już działa jako host (jeśli to zrobisz, istniejący obiekt hosta nie zostanie zwolniona).

Pierwsze siedem funkcji wywołać [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) niejawnie.

> [!NOTE]
> Interfejs API hostingu sterowania stanowi podstawę obsługi ATL dla zamknięcia kontroli ActiveX. Jednak zazwyczaj istnieje niewielka potrzeba wywołania tych funkcji bezpośrednio, jeśli skorzystasz lub w pełni wykorzystasz klasy otoki ATL. Aby uzyskać więcej informacji, zobacz [Które klasy ATL ułatwiają powstrzymywanie kontroli ActiveX](which-atl-classes-facilitate-activex-control-containment-q.md).

## <a name="what-is-atlaxwin100"></a>Co to jest klasa AtlAxWin100?

`AtlAxWin100`to nazwa klasy okna, która pomaga zapewnić funkcję hostingu sterowania ATL. Podczas tworzenia wystąpienia tej klasy, procedura okna automatycznie użyje interfejsu API hostingu formantu, aby utworzyć obiekt hosta skojarzony z oknem i załadować go z formantem, który określisz jako tytuł okna.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>Kiedy muszę tworzyć wywołanie klasy AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) rejestruje klasę okna **"AtlAxWin80"** (plus kilka niestandardowych komunikatów okien), więc ta funkcja musi zostać wywołana przed próbą utworzenia okna hosta. Jednak nie zawsze trzeba wywołać tę funkcję jawnie, ponieważ interfejsy API hostingu (i klasy, które z nich korzystają) często wywołać tę funkcję dla Ciebie. Wywołanie tej funkcji nie ma nic złego.

## <a name="what-is-a-host-object"></a>Co to jest obiekt hosta?

Obiekt hosta jest obiektem COM, który reprezentuje kontener formantu ActiveX dostarczony przez ATL dla określonego okna. Obiekt hosta podklasuje okno kontenera, dzięki czemu może odzwierciedlać komunikaty do formantu, zapewnia niezbędne interfejsy kontenera, które mają być używane przez formant i udostępnia [interfejsy IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) i [IAxWinAmbientDispatch,](../atl/reference/iaxwinambientdispatch-interface.md) aby umożliwić skonfigurowanie środowiska formantu.

Za pomocą obiektu hosta można ustawić właściwości otoczenia kontenera.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Czy mogę umieścić więcej niż jedną kontrolkę w jednym oknie?

Nie jest możliwe hostowanie więcej niż jednego formantu w jednym oknie hosta ATL. Każde okno hosta jest przeznaczone do przechowywania dokładnie jednego formantu naraz (pozwala to na prosty mechanizm obsługi odbicia wiadomości i właściwości otoczenia kontroli). Jednak jeśli potrzebujesz użytkownika, aby wyświetlić wiele formantów w jednym oknie, jest to prosta sprawa, aby utworzyć wiele okien hosta jako elementy podrzędne tego okna.

## <a name="can-i-reuse-a-host-window"></a>Czy mogę ponownie użyć okna hosta?

Nie zaleca się ponownego użycia okien hosta. Aby zapewnić niezawodność kodu, należy powiązać okres istnienia okna hosta z okresem istnienia pojedynczego formantu.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>Kiedy muszę tworzyć wywołanie klasy AtlAxWinTerm?

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) wyrejestrowyje klasę okna **"AtlAxWin80".** Należy wywołać tę funkcję (jeśli nie trzeba już tworzyć okien hosta) po zniszczeniu wszystkich istniejących okien hosta. Jeśli ta funkcja nie zostanie wywołana, klasa okna zostanie automatycznie wyrejestrowana po zakończeniu procesu.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hosting kontrolek ActiveX przy użyciu ATL AXHost

Przykład w tej sekcji pokazuje, jak utworzyć AXHost i jak hostować formant ActiveX przy użyciu różnych funkcji ATL. Pokazuje również, jak uzyskać dostęp do kontroli i ujmuje zdarzenia (przy użyciu [IDispEventImpl)](../atl/reference/idispeventimpl-class.md)z formantu, który jest obsługiwany. Przykład hostuje Calendar kontroli w oknie głównym lub w oknie podrzędnym.

Zwróć uwagę na `USE_METHOD` definicję symbolu. Można zmienić wartość tego symbolu na 1 do 8. Wartość symbolu określa sposób tworzenia formantu:

- Dla wartości parzyste `USE_METHOD`, wywołanie utworzenia podklas hosta okna i konwertuje go na hosta formantu. Dla wartości nieparzystych kod tworzy okno podrzędne, które działa jako host.

- Dla wartości `USE_METHOD` od 1 do 4 dostęp do kontroli i zatopienie zdarzeń są realizowane w wywołaniu, które również tworzy hosta. Wartości między 5 i 8 kwerendy hosta dla interfejsów i podłączyć ujścia.

Oto podsumowanie:

|USE_METHOD|Host|Kontroluj dostęp i zatopienie zdarzeń|Zademonstrowana funkcja|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Okno podrzędne|Jeden krok|CreateControlLicEx|
|2|Okno główne|Jeden krok|AtlAxCreateControlLicEx|
|3|Okno podrzędne|Jeden krok|UtwórzControlEx|
|4|Okno główne|Jeden krok|AtlAxCreateControlEx|
|5|Okno podrzędne|Wiele kroków|CreateControlLic (Twór niesie ze strony|
|6|Okno główne|Wiele kroków|AtlAxCreateControlLic|
|7|Okno podrzędne|Wiele kroków|CreateControl (Kontrola tworzenia)|
|8|Okno główne|Wiele kroków|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Często zadawane pytania dotyczące hermetyzacji sterowania](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[Klasa CAxWindow2T](../atl/reference/caxwindow2t-class.md)<br/>
[Interfejs IAxWinHostWindowlic](../atl/reference/iaxwinhostwindowlic-interface.md)
