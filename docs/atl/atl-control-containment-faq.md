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
ms.openlocfilehash: 693617589f157d352972485396777cec587a5b8f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352703"
---
# <a name="atl-control-containment-faq"></a>Zawieranie kontrolek ALT — Często zadawane pytania

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>Które klasy ATL umożliwiają zawieranie kontrolek ActiveX?

Kod hostingu formantu ATL nie wymaga użycia żadnych klas ATL; można po prostu utworzyć okno **"AtlAxWin80"** i w razie potrzeby użyć interfejsu API hostingu kontroli (Aby uzyskać więcej informacji, zobacz **co to jest interfejs API hostingu kontrolki ATL**. Jednak następujące klasy ułatwiają korzystanie z funkcji zawierania.

|Klasa|Opis|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|Zawija okno **"AtlAxWin80"** , dostarczając metody tworzenia okna, tworzenia kontrolki i/lub dołączania kontrolki do okna i pobierania wskaźników interfejsu na obiekcie hosta.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Zawija okno **"AtlAxWinLic80"** , dostarczając metody tworzenia okna, tworzenia kontrolki i/lub dołączania licencjonowanej kontrolki do okna i pobierania wskaźników interfejsu na obiekcie hosta.|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Działa jako klasa bazowa dla klas formantów ActiveX na podstawie zasobu okna dialogowego. Takie kontrolki mogą zawierać inne kontrolki ActiveX.|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Działa jako klasa bazowa dla klas okien dialogowych na podstawie zasobu okna dialogowego. Takie okna dialogowe mogą zawierać kontrolki ActiveX.|
|[CWindow](../atl/reference/cwindow-class.md)|Dostarcza metodę, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), która zwróci wskaźnik interfejsu na kontrolce, przy POdanym identyfikatorze okna hosta. Ponadto otoki interfejsu API systemu Windows udostępniane przez `CWindow` ogólnie ułatwiają zarządzanie oknami.|

## <a name="what-is-the-atl-control-hosting-api"></a>Co to jest interfejs API hostingu kontrolek ATL?

Interfejs API hostingu formantów ATL to zestaw funkcji, które umożliwiają działanie dowolnego okna jako kontenera kontrolek ActiveX. Te funkcje mogą być statycznie lub dynamicznie połączone z projektem, ponieważ są dostępne jako kod źródłowy i udostępniane przez ATL90.dll. Funkcje hostingu formantów są wymienione w poniższej tabeli.

|Funkcja|Opis|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Tworzy obiekt hosta, łączy go z podanym oknem, a następnie dołącza istniejący formant.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Tworzy obiekt hosta, łączy go z udostępnionym oknem, a następnie ładuje formant.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i hostuje w określonym oknie, podobnie jak [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Tworzy obiekt hosta, łączy go z udostępnionym oknem, a następnie ładuje kontrolkę (umożliwia również skonfigurowanie ujścia zdarzeń).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Tworzy licencjonowany formant ActiveX, inicjuje go i hostuje w określonym oknie, podobnie jak [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Tworzy niemodalne okno dialogowe z zasobu okna dialogowego i zwraca uchwyt okna.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Tworzy modalne okno dialogowe z zasobu okna dialogowego.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Zwraca wskaźnik interfejsu **IUnknown** kontrolki hostowanej w oknie.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Zwraca wskaźnik interfejsu **IUnknown** obiektu hosta połączonego z oknem.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicjuje kod hostingu kontroli.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Odinicjuje kod hostingu kontroli.|

`HWND`Parametry w pierwszych trzech funkcjach muszą być istniejącym oknem (prawie) dowolnego typu. W przypadku wywołania dowolnej z tych trzech funkcji jawnie (zazwyczaj nie jest to konieczne), nie należy przekazywać dojścia do okna, które już działa jako host (w przeciwnym razie istniejący obiekt hosta nie zostanie zwolniony).

Pierwsze siedem funkcji wywołuje [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) niejawnie.

> [!NOTE]
> Interfejs API hostingu kontrolki stanowi podstawę obsługi programu ATL na potrzeby zawierania formantów ActiveX. Jednak zazwyczaj nie trzeba wywoływać tych funkcji bezpośrednio, jeśli korzystasz z systemu lub w pełni korzystasz z klas otoki ATL. Aby uzyskać więcej informacji, zobacz [klasy ATL ułatwiają zawieranie formantów ActiveX](#which-atl-classes-facilitate-activex-control-containment).

## <a name="what-is-atlaxwin100"></a>Co to jest klasa AtlAxWin100?

`AtlAxWin100` to nazwa klasy okna, która pomaga zapewnić funkcje hostingu formantów ATL. Podczas tworzenia wystąpienia tej klasy, procedura okna automatycznie użyje interfejsu API hostingu kontroli w celu utworzenia obiektu hosta skojarzonego z oknem i załadowania go z kontrolką określoną jako tytuł okna.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>Kiedy muszę tworzyć wywołanie klasy AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) rejestruje klasę okna **"AtlAxWin80"** (oraz kilka niestandardowych komunikatów okien), więc ta funkcja musi zostać wywołana przed podjęciem próby utworzenia okna hosta. Jednak nie zawsze trzeba jawnie wywołać tę funkcję, ponieważ interfejsy API hostowania (i klasy, które ich używają) często wywołują tę funkcję. Nie ma szkody w wywołaniu tej funkcji więcej niż raz.

## <a name="what-is-a-host-object"></a>Co to jest obiekt hosta?

Obiekt hosta jest obiektem COM, który reprezentuje kontener kontrolki ActiveX dostarczony przez ATL dla określonego okna. Obiekt hosta podklasa okna kontenera, dzięki czemu może odzwierciedlać komunikaty do kontrolki, udostępnia interfejsy kontenera niezbędne do użycia przez formant i udostępnia interfejsy [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) i [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) umożliwiające skonfigurowanie środowiska formantu.

Obiekt hosta służy do ustawiania właściwości otoczenia kontenera.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Czy mogę umieścić więcej niż jedną kontrolkę w jednym oknie?

Nie można hostować więcej niż jednej kontrolki w jednym oknie hosta ATL. Każde okno hosta jest przeznaczone do jednoczesnego przechowywania dokładnie jednej kontrolki (pozwala to na prosty mechanizm obsługi odbicia komunikatów i właściwości otoczenia dla kontrolek). Jeśli jednak potrzebujesz, aby użytkownik widział wiele kontrolek w jednym oknie, jest to prosta kwestia, aby utworzyć wiele okien hosta jako elementy podrzędne tego okna.

## <a name="can-i-reuse-a-host-window"></a>Czy mogę ponownie użyć okna hosta?

Nie zaleca się ponownego użycia okien hosta. Aby zapewnić niezawodność kodu, należy powiązać okres istnienia Twojego okna hosta z okresem istnienia pojedynczej kontrolki.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>Kiedy muszę tworzyć wywołanie klasy AtlAxWinTerm?

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) wyrejestrowuje klasę okna **"AtlAxWin80"** . Należy wywołać tę funkcję (jeśli nie musisz już tworzyć okien hosta) po zniszczeniu wszystkich istniejących okien hosta. Jeśli ta funkcja nie zostanie wywołana, Klasa Window zostanie wyrejestrowana automatycznie po zakończeniu procesu.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hosting kontrolek ActiveX przy użyciu ATL AXHost

W przykładzie w tej sekcji pokazano, jak utworzyć AXHost oraz jak hostować kontrolkę ActiveX przy użyciu różnych funkcji ATL. Pokazano również, jak uzyskać dostęp do zdarzeń kontrolki i ujścia (przy użyciu [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) z obsługiwanej kontrolki. Przykład zawiera kontrolkę Calendar w oknie głównym lub w oknie podrzędnym.

Zwróć uwagę na definicję `USE_METHOD` symbolu. Można zmienić wartość tego symbolu, aby różnić się od 1 do 8. Wartość symbolu określa sposób, w jaki formant zostanie utworzony:

- W przypadku wartości z parzystością `USE_METHOD` , wywołanie do tworzenia podklasy hosta i przekształca je na host kontrolny. W przypadku wartości numerowanych nieparzyste kod tworzy okno podrzędne, które działa jako host.

- W przypadku wartości z `USE_METHOD` zakresu od 1 do 4 dostęp do kontrolki i ujścia zdarzeń są wykonywane w wywołaniu, które również tworzy hosta. Wartości z przedziału od 5 do 8 wyszukują interfejsy i przechwytuje ujścia.

Oto podsumowanie:

|USE_METHOD|Host|Kontrola dostępu i ujścia zdarzeń|Pokazana funkcja|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Okno podrzędne|Jeden krok|CreateControlLicEx|
|2|Okno główne|Jeden krok|AtlAxCreateControlLicEx|
|3|Okno podrzędne|Jeden krok|CreateControlEx|
|4|Okno główne|Jeden krok|AtlAxCreateControlEx|
|5|Okno podrzędne|Wiele kroków|Moje kontrolowane|
|6|Okno główne|Wiele kroków|AtlAxCreateControlLic|
|7|Okno podrzędne|Wiele kroków|Formant kontrolny|
|8|Okno główne|Wiele kroków|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki zawierania — często zadawane pytania](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[Klasa CAxWindow2T](../atl/reference/caxwindow2t-class.md)<br/>
[IAxWinHostWindowLic, interfejs](../atl/reference/iaxwinhostwindowlic-interface.md)
