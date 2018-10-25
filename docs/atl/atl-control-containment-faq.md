---
title: Zawieranie kontrolek ATL — często zadawane pytania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af14755b9be9413feb3a519d09200577c9260c5a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053712"
---
# <a name="atl-control-containment-faq"></a>Zawieranie kontrolek ALT — Często zadawane pytania

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>Które klasy ATL umożliwiają zawieranie kontrolek ActiveX?

Kod hostingu formantu ATL nie wymagają użycia dowolnej klasy ATL; Możesz po prostu utworzyć **"AtlAxWin80"** okno i użyj interfejsu API hostingu kontrolek w razie potrzeby (Aby uzyskać więcej informacji, zobacz **co to jest interfejs API hostingu kontrolek ATL**. Jednak następujące klasy ułatwić funkcjami zawierania do użycia.

|Class|Opis|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|Opakowuje **"AtlAxWin80"** okna, zapewniając metody do tworzenia okna, tworzenie formantu i/lub dołączanie formantu do okna i pobierania wskaźniki interfejsu na obiekt hosta.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Opakowuje **"AtlAxWinLic80"** okna, zapewniając metody do tworzenia okna, tworzenie formantu i/lub dołączanie licencjonowany formant do okna i pobierania wskaźniki interfejsu na obiekt hosta.|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Działa jako klasę bazową dla klasy kontrolek ActiveX w oparciu o zasobu okna dialogowego. Takie kontrolki mogą zawierać inne kontrolki ActiveX.|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Działa jako klasę bazową dla klasy okien dialogowych, w oparciu o zasobu okna dialogowego. Takie okien dialogowych mogą zawierać formantów ActiveX.|
|[CWindow](../atl/reference/cwindow-class.md)|Udostępnia metodę, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), które zwróci wskaźnika interfejsu sterowanie podany identyfikator hosta okna. Ponadto otoki interfejsu Windows API udostępnianych przez `CWindow` ogólnie ułatwić zarządzanie oknem.|

## <a name="what-is-the-atl-control-hosting-api"></a>Co to jest ATL Hosting kontrolki interfejsu API?

ATL użytkownika hosting kontrolki interfejsu API to zestaw funkcji, który umożliwia dowolnym oknie jako kontener formantu ActiveX. Te funkcje mogą być statycznie lub dynamicznie połączone do projektu, ponieważ są one dostępne jako kod źródłowy i udostępnianych przez ATL90.dll. Funkcje hostingu kontrolek są wymienione w poniższej tabeli.

|Funkcja|Opis|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Tworzy obiekt hosta, łączy się ono podane okna, a następnie dołącza istniejącej kontrolki.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Tworzy obiekt hosta, łączy się ono podane okna, a następnie ładuje formantu.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie, podobnie jak [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Tworzy obiekt hosta, łączy się ono podane okna, a następnie ładuje kontrolki (również pozwala wychwytywanie zdarzeń do skonfigurowania).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie, podobnie jak [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Tworzy niemodalne okno dialogowe z zasobu okna dialogowego i zwraca uchwyt okna.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Tworzy modalne okno dialogowe z zasobu okna dialogowego.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Zwraca **IUnknown** wskaźnika interfejsu tego formantu w oknie.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Zwraca **IUnknown** wskaźnika interfejsu tego obiektu hosta jest podłączony do okna.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicjuje kod hostingu formantu.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Deinicjuje kod hostingu formantu.|

`HWND` Parametrów w pierwszych trzech funkcji musi być istniejącym oknie (prawie) dowolnego typu. Jeśli dowolny z tych trzech funkcji jawnie wywołać (zazwyczaj nie trzeba), nie przekazuj dojścia do okna, która już działa jako host (Jeśli to zrobisz, istniejący obiekt hosta nie można zwolnić).

Wywołaj najpierw siedmiu funkcji [klasy AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) niejawnie.

> [!NOTE]
>  Interfejs API hostingu kontrolek stanowi podstawę ATL obsługę zawierania kontrolek ActiveX. Istnieje jednak zwykle nieco trzeba bezpośrednio wywoływać tych funkcji, jeśli korzystanie z zalet lub wykorzystać ATL klasy otoki. Aby uzyskać więcej informacji, zobacz [której klasy ułatwienia ActiveX zawieranie kontrolek ATL](which-atl-classes-facilitate-activex-control-containment-q.md).

## <a name="what-is-atlaxwin100"></a>Co to jest klasa AtlAxWin100?

`AtlAxWin100` jest nazwą klasy okna, który zapewnia funkcje hostingu kontrolek ATL. Podczas tworzenia wystąpienia tej klasy procedurę okna automatycznie używać interfejsu API hostingu kontrolek do tworzenia obiektu hosta skojarzony z oknem i ją załadować za pomocą kontrolki, które można określić jako tytuł okna.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>Kiedy muszę tworzyć wywołanie klasy AtlAxWinInit?

[Klasy AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) rejestruje **"AtlAxWin80"** klasy okna (oraz kilka niestandardowych komunikatów okien), dzięki czemu można wywołać tę funkcję, przed podjęciem próby utworzenia okna hosta. Jednak nie należy zawsze jawnie wywołać tę funkcję, od hostowania interfejsów API (i klas, które z nich korzystają) często wymagają tej funkcji. Nie ma żadnych szkód w wywołaniu tej funkcji w więcej niż jeden raz.

## <a name="what-is-a-host-object"></a>Co to jest obiekt hosta?

Obiekt hosta jest obiekt COM, który reprezentuje kontener formantu ActiveX, które są dostarczane przez ATL dla określonego okna. Hosta obiektu podklasy okno kontenera, aby go może odzwierciedlać wiadomości do formantu, zapewnia interfejsy niezbędne kontenera, który ma być używany przez formant i udostępnia ona [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) i [ IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) interfejsy umożliwiają skonfigurowanie środowiska formantu.

Obiekt hosta służy do ustawiania właściwości otoczenia kontenera.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Czy może obsługiwać więcej niż jeden formant w jednym oknie?

Nie jest możliwe do hostowania więcej niż jeden formant w jednym oknie ATL, hosta. Każde okno hosta powinien zawierać dokładnie jeden formant naraz (umożliwia to prosty mechanizm obsługi odbicia i -control otoczenia właściwości wiadomości). Jednak jeśli potrzebujesz użytkownika, aby wyświetlić wiele kontrolek w jednym oknie, jest polegać, aby utworzyć wiele okien hosta jako elementy podrzędne tego okna.

## <a name="can-i-reuse-a-host-window"></a>Czy mogę ponownie użyć okna hosta?

Ponowne użycie systemu windows hosta nie jest zalecane. Aby zapewnić niezawodność kodu, należy powiązać okres istnienia okna hosta z okresem istnienia jeden formant.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>Kiedy muszę tworzyć wywołanie klasy AtlAxWinTerm?

[Klasy AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) wyrejestrowuje **"AtlAxWin80"** klasy okna. Należy wywołać tę funkcję (Jeśli nie jest już konieczne tworzenie hosta z systemem windows) po zniszczeniu wszystkich istniejących okien hosta. Jeśli nie chcesz wywołać tę funkcję, klasę okna będzie można wyrejestrować automatycznie, gdy proces zakończy się.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hosting kontrolek ActiveX przy użyciu ATL AXHost

Przykład w tej sekcji przedstawiono sposób tworzenia AXHost oraz sposobu hostowania kontrolki ActiveX przy użyciu różnych funkcji biblioteki ATL. Zawiera również instrukcje zdarzenia sink i kontroli dostępu (przy użyciu [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) z formantu, który znajduje się. Przykład obsługuje formant kalendarza w głównym oknie lub okna podrzędnego.

Zwróć uwagę, definicja `USE_METHOD` symboli. Możesz zmienić wartość tego symbolu będzie się różnić od 1 do 8. Wartość symbolu określa sposób tworzenia kontrolki:

- Wartości parzystych `USE_METHOD`, wywołanie w celu utworzenia podklasy hosta okna i konwertuje je do hosta kontroli. W przypadku wartości nieparzystą kod tworzy okno podrzędne, który działa jako host.

- Wartości typu `USE_METHOD` od 1 do 4, dostęp do formantu i wychwytywania zdarzeń są wykonywane w wywołaniu, który również tworzy hosta. Wartości z zakresu od 5 do 8 zapytania hosta dla interfejsów i podłączyć ujścia.

Poniżej przedstawiono podsumowanie:

|USE_METHOD|Host|Kontrola dostępu i wychwytywania zdarzeń|Pokazano — funkcja|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Okno podrzędne|Jeden krok|CreateControlLicEx|
|2|Okno główne|Jeden krok|AtlAxCreateControlLicEx|
|3|Okno podrzędne|Jeden krok|CreateControlEx|
|4|Okno główne|Jeden krok|AtlAxCreateControlEx|
|5|Okno podrzędne|Wiele kroków|CreateControlLic|
|6|Okno główne|Wiele kroków|AtlAxCreateControlLic|
|7|Okno podrzędne|Wiele kroków|CreateControl —|
|8|Okno główne|Wiele kroków|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Zawieranie kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[Klasa CAxWindow2T](../atl/reference/caxwindow2t-class.md)<br/>
[Interfejs IAxWinHostWindowLic](../atl/reference/iaxwinhostwindowlic-interface.md)