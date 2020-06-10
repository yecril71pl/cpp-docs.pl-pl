---
title: MFC — implementacja paska narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
ms.openlocfilehash: 7876e9403389c19a24e5a482534d0f223eaa4bf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626116"
---
# <a name="mfc-toolbar-implementation"></a>MFC — implementacja paska narzędzi

Pasek narzędzi jest [paskiem sterowania](control-bars.md) , który zawiera obrazy mapy bitowej kontrolek. Obrazy te mogą zachowywać się w taki sam sposób, jak przyciski, pola wyboru lub przycisk radiowy. MFC dostarcza klasy [CToolBar](reference/ctoolbar-class.md) do zarządzania paskami narzędzi.

Jeśli włączysz tę funkcję, użytkownicy narzędzi MFC mogą zadokować je na krawędzi okna lub "float" w dowolnym miejscu w oknie aplikacji. MFC nie obsługuje dostosowywalnych pasków narzędzi, takich jak te w środowisku deweloperskim.

MFC obsługuje również etykietki narzędzi: małe okna podręczne, które opisują przeznaczenie przycisku paska narzędzi po umieszczeniu wskaźnika myszy nad przyciskiem. Domyślnie, gdy użytkownik naciśnie przycisk paska narzędzi, na pasku stanu pojawi się ciąg stanu (jeśli istnieje). Można uaktywnić aktualizację paska stanu "przylot", aby wyświetlić ciąg stanu, gdy wskaźnik myszy znajduje się nad przyciskiem bez naciskania.

> [!NOTE]
> Począwszy od wersji 4,0, paski narzędzi i wskazówki dotyczące narzędzi są implementowane przy użyciu systemu Windows 95 i nowszych funkcji zamiast poprzedniej implementacji specyficznej dla MFC.

W celu zapewnienia zgodności z poprzednimi wersjami MFC zachowuje starszą implementację paska narzędzi w klasie `COldToolBar` . Dokumentacja dotycząca wcześniejszych wersji MFC została opisywana `COldToolBar` w sekcji `CToolBar` .

Utwórz pierwszy pasek narzędzi w programie, wybierając opcję Pasek narzędzi w Kreatorze aplikacji. Możesz również utworzyć dodatkowe paski narzędzi.

W tym artykule wprowadzono następujące elementy:

- [Przyciski paska narzędzi](#_core_toolbar_buttons)

- [Dokowanie i przestawne paski narzędzi](#_core_docking_and_floating_toolbars)

- [Paski narzędzi i wskazówki dotyczące narzędzi](#_core_toolbars_and_tool_tips)

- [Klasy CToolBar i CToolBarCtrl](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [Mapa bitowa paska narzędzi](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a>Przyciski paska narzędzi

Przyciski na pasku narzędzi są analogiczne do elementów w menu. Oba rodzaje obiektów interfejsu użytkownika generują polecenia, które są obsługiwane przez program, dostarczając funkcje obsługi. Często przyciski paska narzędzi duplikują funkcje poleceń menu, zapewniając alternatywny interfejs użytkownika w tej samej funkcji. Takie duplikowanie jest ułożone po prostu, dając przycisk i element menu tego samego identyfikatora.

Można sprawić, aby przyciski na pasku narzędzi pojawiły się i zachowywać się jako przyciski, pola wyboru lub przycisk radiowy. Aby uzyskać więcej informacji, zobacz Klasa [CToolBar](reference/ctoolbar-class.md).

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a>Dokowanie i przestawne paski narzędzi

Pasek narzędzi MFC może:

- Pozostaje nieruchoma wzdłuż jednej strony okna nadrzędnego.

- Być przeciągane i "zadokowane" lub dołączone, przez użytkownika do dowolnej krawędzi okna nadrzędnego, którą określisz.

- Być "zmiennoprzecinkowe" lub odłączone od okna ramki w osobnym oknie mini-frame, dzięki czemu użytkownik może je przenieść do dowolnego wygodnego położenia.

- Rozmiar zmienia się podczas operacji zmiennoprzecinkowych.

Aby uzyskać więcej informacji, zapoznaj się z artykułem [dokowanie i przestawne paski narzędzi](docking-and-floating-toolbars.md).

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a>Paski narzędzi i wskazówki dotyczące narzędzi

Można również udostępnić paski narzędzi MFC, aby wyświetlać "etykietki narzędzi" — małe okna podręczne zawierające Krótki opis tekstu przeznaczenie przycisku paska narzędzi. Gdy użytkownik przesuwa wskaźnik myszy nad przyciskiem paska narzędzi, okna etykietki narzędzia pojawiają się, aby zaoferować wskazówkę. Aby uzyskać więcej informacji, zobacz [wskazówki dotyczące narzędzia paska narzędzi](toolbar-tool-tips.md)artykułów.

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>Klasy CToolBar i CToolBarCtrl

Możesz zarządzać paskami narzędzi aplikacji za pomocą klasy [CToolBar](reference/ctoolbar-class.md). Od wersji 4,0 programu MFC `CToolBar` została zaimplementowana ponownie w celu użycia typowej kontrolki paska narzędzi dostępnej w systemie windows 95 lub nowszym oraz w systemie Windows NT w wersji 3,51 lub nowszej.

Ta Reimplementacja powoduje przeprowadzenie mniej kodu MFC dla pasków narzędzi, ponieważ MFC korzysta z obsługi systemu operacyjnego. Ponadto ta funkcja poprawia możliwości. Za pomocą `CToolBar` funkcji składowych można manipulować paskami narzędzi lub można uzyskać odwołanie do bazowego obiektu [CToolBarCtrl](reference/ctoolbarctrl-class.md) i wywoływać funkcje składowe w celu dostosowania paska narzędzi i dodatkowych funkcji.

> [!TIP]
> Jeśli zainwestowano w starszą wersję MFC implementacji `CToolBar` , to pomoc techniczna jest nadal dostępna. Zobacz artykuł, [używając starych pasków narzędzi](using-your-old-toolbars.md).

Zobacz również ogólne przykładowe [DOCKTOOL](../overview/visual-cpp-samples.md)MFC.

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a>Mapa bitowa paska narzędzi

Po skonstruowaniu `CToolBar` obiekt tworzy obraz paska narzędzi, ładując pojedynczą mapę bitową, która zawiera jeden obraz dla każdego przycisku. Kreator aplikacji tworzy standardową mapę bitową paska narzędzi, którą można dostosować za pomocą [edytora paska narzędzi](../windows/toolbar-editor.md)Visual C++.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Podstawy paska narzędzi](toolbar-fundamentals.md)

- [Dokowanie i przestawne paski narzędzi](docking-and-floating-toolbars.md)

- [Wskazówki dotyczące narzędzia paska narzędzi](toolbar-tool-tips.md)

- [Praca z kontrolką paska narzędzi](working-with-the-toolbar-control.md)

- [Używanie swoich starych pasków narzędzi](using-your-old-toolbars.md)

- Klasy [CToolBar](reference/ctoolbar-class.md) i [CToolBarCtrl](reference/ctoolbarctrl-class.md)

## <a name="see-also"></a>Zobacz też

[Paski narzędzi](toolbars.md)<br/>
[Edytor paska narzędzi](../windows/toolbar-editor.md)
