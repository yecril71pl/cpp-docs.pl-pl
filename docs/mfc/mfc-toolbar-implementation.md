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
ms.openlocfilehash: 38811be765d4427c4083b8f142b54fb67b9076a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359320"
---
# <a name="mfc-toolbar-implementation"></a>MFC — implementacja paska narzędzi

Pasek narzędzi to [pasek sterowania](../mfc/control-bars.md) zawierający obrazy bitmapowe formantów. Te obrazy mogą zachowywać się jak przyciski, pola wyboru lub przyciski radiowe. MFC dostarcza klasy [CToolbar](../mfc/reference/ctoolbar-class.md) do zarządzania paskami narzędzi.

Jeśli go włączyć, użytkownicy pasków narzędzi MFC można zadokować je do krawędzi okna lub "float" je w dowolnym miejscu w oknie aplikacji. MFC nie obsługuje konfigurowalnych pasków narzędzi, takich jak te w środowisku programistycznym.

MFC obsługuje również porady dotyczące narzędzi: małe wyskakujące okna, które opisują cel przycisku paska narzędzi podczas położenia myszy na przycisku. Domyślnie, gdy użytkownik naciśnie przycisk paska narzędzi, na pasku stanu pojawi się ciąg stanu (jeśli istnieje). Możesz aktywować pasek stanu "fly by", aktualizując, aby wyświetlić ciąg stanu, gdy mysz jest mieszczona nad przyciskiem bez naciskania go.

> [!NOTE]
> W wersji MFC 4.0 paski narzędzi i porady narzędzia są implementowane przy użyciu systemu Windows 95 i nowszych funkcji zamiast poprzedniej implementacji specyficzne dla MFC.

W celu zapewnienia zgodności z powrotem MFC zachowuje `COldToolBar`starszą implementację paska narzędzi w klasie . Dokumentacja dla wcześniejszych wersji `COldToolBar` MFC opisano w obszarze `CToolBar`.

Utwórz pierwszy pasek narzędzi w programie, wybierając opcję Pasek narzędzi w Kreatorze aplikacji. Można również utworzyć dodatkowe paski narzędzi.

W tym artykule przedstawiono następujące informacje:

- [Przyciski paska narzędzi](#_core_toolbar_buttons)

- [Dokowanie i pływające paski narzędzi](#_core_docking_and_floating_toolbars)

- [Paski narzędzi i wskazówki dotyczące narzędzi](#_core_toolbars_and_tool_tips)

- [Klasy CToolBar i CToolBarCtrl](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [Mapa bitowa paska narzędzi](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a>Przyciski paska narzędzi

Przyciski na pasku narzędzi są analogiczne do elementów w menu. Oba rodzaje obiektów interfejsu użytkownika generują polecenia, które program obsługuje, udostępniając funkcje obsługi. Często przyciski paska narzędzi powielają funkcjonalność poleceń menu, zapewniając alternatywny interfejs użytkownika do tej samej funkcji. Takie powielanie jest ułożone po prostu przez nadanie przycisku i pozycji menu tego samego identyfikatora.

Przyciski na pasku narzędzi mogą być wyświetlane i zachowywać się jak przyciski, pola wyboru lub przyciski radiowe. Aby uzyskać więcej informacji, zobacz klasę [CToolBar](../mfc/reference/ctoolbar-class.md).

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a>Dokowanie i pływające paski narzędzi

Pasek narzędzi MFC może:

- Pozostają nieruchome wzdłuż jednej strony okna nadrzędnego.

- Być przeciągane i "zadokowane" lub dołączone przez użytkownika do dowolnej strony lub boków okna nadrzędnego, które określisz.

- Być "floated", lub odłączony od okna ramy, we własnym oknie mini-ramki, dzięki czemu użytkownik może przenieść go do dowolnej wygodnej pozycji.

- Można zwymiarować podczas pływających.

Aby uzyskać więcej informacji, zobacz artykuł [Dokowanie i pływające paski narzędzi](../mfc/docking-and-floating-toolbars.md).

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a>Paski narzędzi i wskazówki dotyczące narzędzi

Paski narzędzi MFC mogą być również wykonane, aby wyświetlić "porady narzędzia" - małe okna podręczne zawierające krótki opis tekstowy celu przycisku paska narzędzi. Gdy użytkownik przesuwa kursor myszy nad przyciskiem paska narzędzi, pojawia się okno etykietki narzędzia, aby zaoferować wskazówkę. Aby uzyskać więcej informacji, zobacz artykuł [Porady dotyczące narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md).

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>Klasy CToolBar i CToolBarCtrl

Zarządzasz paskami narzędzi aplikacji za pośrednictwem klasy [CToolBar](../mfc/reference/ctoolbar-class.md). Od wersji MFC 4.0, `CToolBar` został ponownie zaimplementowany do korzystania z wspólnego formantu paska narzędzi dostępnego w systemie Windows 95 lub nowszym i Windows NT w wersji 3.51 lub nowszej.

To ponowneimplementowanie powoduje mniej kodu MFC dla pasków narzędzi, ponieważ MFC korzysta z obsługi systemu operacyjnego. Ponowneimplementacja zwiększa również możliwości. Za pomocą `CToolBar` funkcji członkowskich można manipulować paskami narzędzi lub można uzyskać odwołanie do podstawowego [obiektu CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) i wywołać jego funkcje członkowskie w celu dostosowania paska narzędzi i dodatkowych funkcji.

> [!TIP]
> Jeśli zainwestowałeś dużo w starsze wdrożenie `CToolBar`MFC , to wsparcie jest nadal dostępne. Zobacz artykuł [Korzystanie ze starych pasków narzędzi](../mfc/using-your-old-toolbars.md).

Zobacz także przykładowy [docktool](../overview/visual-cpp-samples.md)MFC General .

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a>Mapa bitowa paska narzędzi

Po skonstruowaniu `CToolBar` obiekt tworzy obraz paska narzędzi, ładując pojedynczą mapę bitową zawierającą jeden obraz dla każdego przycisku. Kreator aplikacji tworzy standardową mapę bitową paska narzędzi, którą można dostosować za pomocą [edytora paska narzędzi](../windows/toolbar-editor.md)Visual C++ .

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Podstawy paska narzędzi](../mfc/toolbar-fundamentals.md)

- [Dokowanie i pływające paski narzędzi](../mfc/docking-and-floating-toolbars.md)

- [Wskazówki dotyczące narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)

- [Praca z kontrolką paska narzędzi](../mfc/working-with-the-toolbar-control.md)

- [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

- Klasy [CToolBar](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

## <a name="see-also"></a>Zobacz też

[Paski narzędzi](../mfc/toolbars.md)<br/>
[Edytor paska narzędzi](../windows/toolbar-editor.md)
