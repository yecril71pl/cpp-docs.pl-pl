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
ms.openlocfilehash: 55c43c47b93cd21d86293706fc7c3eb5145c39fd
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773180"
---
# <a name="mfc-toolbar-implementation"></a>MFC — implementacja paska narzędzi

Pasek narzędzi jest [pasek sterowania](../mfc/control-bars.md) zawierający obrazy mapy bitowej kontrolek. Te obrazy mogą zachowywać się jak przyciski, pola wyboru lub przycisków radiowych. MFC udostępnia klasy [CToolbar](../mfc/reference/ctoolbar-class.md) Zarządzanie pasków narzędzi.

Jeśli zostanie włączone, użytkownicy pasków narzędzi MFC można zadokować je do krawędzi okna lub "zwalniać" dowolne miejsce w oknie aplikacji. MFC nie obsługuje dostosowywalnych pasków narzędzi, takich jak te w środowisku programistycznym.

Biblioteka MFC obsługuje etykietek narzędzi: mały wyskakującego okienka, które opisują cel przycisku paska narzędzi, gdy umieść wskaźnik myszy na przycisku. Domyślnie gdy użytkownik naciśnie przycisk paska narzędzi, ciąg stanu pojawia się na pasku stanu (jeśli istnieje). Możesz aktywować paska aktualizowanie wyświetlany ciąg stanu, gdy wskaźnik myszy znajduje się nad przyciskiem bez jego naciśnięcie "bieżąco przez" stanu.

> [!NOTE]
>  Począwszy od wersji 4.0 MFC paski narzędzi i etykietek narzędzi są implementowane przy użyciu Windows 95 i nowsze funkcje zamiast poprzedniej implementacji MFC.

W celu zapewnienia zgodności z poprzednimi wersjami MFC zachowuje starsze implementacja paska narzędzi w klasie `COldToolBar`. Opisz dokumentacji dla wcześniejszych wersji MFC `COldToolBar` w obszarze `CToolBar`.

Utwórz pierwszą narzędzi w programach, wybierając opcję narzędzi w Kreatorze aplikacji. Można również utworzyć dodatkowe paski narzędzi.

Poniżej zostały wprowadzone w tym artykule:

- [Przyciski paska narzędzi](#_core_toolbar_buttons)

- [Zadokowane i przestawne paski narzędzi](#_core_docking_and_floating_toolbars)

- [Paski narzędzi i etykietek narzędzi](#_core_toolbars_and_tool_tips)

- [Klasy CToolBar i CToolBarCtrl](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [Mapy bitowej paska narzędzi](#_core_the_toolbar_bitmap)

##  <a name="_core_toolbar_buttons"></a> Przyciski paska narzędzi

Przyciski na pasku narzędzi są analogiczne do tych elementów w menu. Oba rodzaje obiektów interfejsu użytkownika Generowanie poleceń, które obsługuje program, udostępniając funkcje obsługi. Często przycisków paska narzędzi zduplikowane funkcjonalność polecenia menu, zapewniając interfejsu użytkownika alternatywnych taką samą funkcjonalność. Takie duplikowanie rozmieszczone po prostu dając przycisku i element menu ten sam identyfikator.

Można tworzyć przyciski na pasku narzędzi są wyświetlane i zachowują się jak przyciski, pola wyboru lub przycisków radiowych. Aby uzyskać więcej informacji, zobacz klasy [CToolBar](../mfc/reference/ctoolbar-class.md).

##  <a name="_core_docking_and_floating_toolbars"></a> Zadokowane i przestawne paski narzędzi

Pasek narzędzi MFC wykonywać następujące czynności:

- Pozostają stacjonarnych po jednej stronie okna nadrzędnego.

- Przeciąganie i "zadokowane" lub dołączone przez użytkownika do dowolnej strony lub stron okna nadrzędnego, należy określić.

- "Przestawione" lub odłączyć od okno ramowe w osobnym oknie mini ramki, więc użytkownik go przenieść w odpowiednim miejscu.

- Można zmienić rozmiaru podczas liczb zmiennoprzecinkowych.

Aby uzyskać więcej informacji, zobacz artykuł [dokowanie i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md).

##  <a name="_core_toolbars_and_tool_tips"></a> Paski narzędzi i etykietek narzędzi

Paski narzędzi MFC można również wyświetlić "etykietki narzędzi" — niewielki rozmiar okna podręcznego systemu windows, zawierający krótki opis przeznaczenia przycisku paska narzędzi. Gdy użytkownik przesuwa wskaźnik myszy na przycisku paska narzędzi, okno porad narzędzia pojawia się oferują wskazówką. Aby uzyskać więcej informacji, zobacz artykuł [etykietki narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md).

##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a> CToolBar i klasy CToolBarCtrl

Zarządzanie pasków narzędzi aplikacji, za pomocą klasy [CToolBar](../mfc/reference/ctoolbar-class.md). Począwszy od wersji 4.0, MFC `CToolBar` ma zostać reimplemented używać formantu typowego paska narzędzi dostępnych w ramach Windows 95 lub nowszym i Windows NT w wersji 3.51 lub nowszej.

Ta reimplementation skutkuje mniejszej ilości kodu MFC dla pasków narzędzi, ponieważ MFC sprawia, że korzystanie z pomocy technicznej systemu operacyjnego. Reimplementation zwiększa również możliwości. Możesz użyć `CToolBar` elementów członkowskich do manipulowania paski narzędzi, lub można uzyskać odwołanie do bazowej [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiektu i wywoływać funkcje członków pasków narzędzi i dodatkowe funkcje.

> [!TIP]
>  Jeśli użytkownik zainwestowali intensywnie w starszych implementacji MFC `CToolBar`, czy pomoc techniczna jest nadal dostępna. Zapoznaj się z artykułem [przy użyciu usługi starych pasków narzędzi](../mfc/using-your-old-toolbars.md).

Zobacz też próbki MFC-ogólne [DOCKTOOL](../overview/visual-cpp-samples.md).

##  <a name="_core_the_toolbar_bitmap"></a> Mapy bitowej paska narzędzi

Raz wykonane, `CToolBar` obiektu tworzy obraz paska narzędzi, ładując bitmapy, który zawiera jeden obraz dla każdego przycisku. Kreator aplikacji tworzy mapę bitową standardowy pasek narzędzi, które można dostosować za pomocą języka Visual C++ [Edytor paska narzędzi](../windows/toolbar-editor.md).

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Podstawowe informacje dotyczące narzędzi](../mfc/toolbar-fundamentals.md)

- [Zadokowane i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md)

- [Etykietki narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)

- [Praca z kontrolką paska narzędzi](../mfc/working-with-the-toolbar-control.md)

- [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) klas

## <a name="see-also"></a>Zobacz także

[Paski narzędzi](../mfc/toolbars.md)<br/>
[Edytor paska narzędzi](../windows/toolbar-editor.md)
