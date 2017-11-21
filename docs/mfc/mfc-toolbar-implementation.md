---
title: "MFC — implementacja paska narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: defb0dc6faa5438dc7f040fbd09f318b60b5a2ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-toolbar-implementation"></a>MFC — implementacja paska narzędzi
Pasek narzędzi jest [pasek sterowania](../mfc/control-bars.md) zawierający obrazy mapy bitowej kontrolek. Tych obrazów, może zachowywać się jak przyciski, pola wyboru lub przycisków radiowych. Klasa dostarcza MFC [ctoolbar —](../mfc/reference/ctoolbar-class.md) do zarządzania pasków narzędzi.  
  
 Jeśli zostanie włączone, użytkownicy paski narzędzi MFC może dock je do krawędzi okna lub "float" ich dowolne miejsce w oknie aplikacji. MFC nie obsługuje dostosowywalnych pasków narzędzi, takich jak te w środowisku programistycznym.  
  
 Etykietki narzędzi obsługuje również MFC: małe okienka wyskakujące opisujące cel przycisku paska narzędzi, gdy umieszczenie wskaźnika myszy nad przyciskiem. Domyślnie gdy użytkownik naciśnie przycisk paska narzędzi, ciąg stanu pojawia się w pasku stanu (jeśli istnieje). Może aktywować pasek aktualizowanie wyświetlany ciąg stanu, gdy wskaźnik myszy znajduje się nad przyciskiem bez jego naciśnięcie stanu "Przylot przez".  
  
> [!NOTE]
>  Począwszy od wersji 4.0 MFC pasków narzędzi i etykietki narzędzi są implementowane za pomocą systemu Windows 95 i nowsze funkcje zamiast poprzedniej implementacji MFC.  
  
 W celu zapewnienia zgodności z poprzednimi wersjami MFC zachowuje starsze implementacja paska narzędzi w klasie **coldtoolbar —**. Opisz dokumentacji dla wcześniejszych wersji MFC **coldtoolbar —** w obszarze `CToolBar`.  
  
 Utworzenie pierwszego paska narzędzi w programie przez wybranie opcji narzędzi w Kreatorze aplikacji. Można również utworzyć dodatkowe paski narzędzi.  
  
 Poniżej zostały wprowadzone w tym artykule:  
  
-   [Przyciski paska narzędzi](#_core_toolbar_buttons)  
  
-   [Zadokowane i przestawne paski narzędzi](#_core_docking_and_floating_toolbars)  
  
-   [Paski narzędzi i etykietki narzędzi](#_core_toolbars_and_tool_tips)  
  
-   [Ctoolbar — i ctoolbarctrl — klasy](#_core_the_ctoolbar_and_ctoolbarctrl_classes)  
  
-   [Mapa bitowa paska narzędzi](#_core_the_toolbar_bitmap)  
  
##  <a name="_core_toolbar_buttons"></a>Przyciski paska narzędzi  
 Przyciski na pasku narzędzi są analogiczne do tych elementów w menu. Oba rodzaje obiektów interfejsu użytkownika generowania poleceń, które obsługuje program, udostępniając funkcje programu obsługi. Często przycisków paska narzędzi powielają funkcjonalność poleceń menu, udostępnia interfejs użytkownika alternatywnych do funkcji. Takiego dublowania są rozmieszczone po prostu zapewniając przycisk, a element menu ten sam identyfikator.  
  
 Można zwiększyć przycisków na pasku narzędzi są wyświetlane i zachowywać się jak przyciski, pola wyboru lub przycisków radiowych. Aby uzyskać więcej informacji, zobacz klasy [ctoolbar —](../mfc/reference/ctoolbar-class.md).  
  
##  <a name="_core_docking_and_floating_toolbars"></a>Zadokowane i przestawne paski narzędzi  
 Pasek narzędzi MFC wykonywać następujące czynności:  
  
-   Spędzić w bezruchu na jednej stronie okna nadrzędnego.  
  
-   Przeciągnąć i "zadokowane" lub dołączone przez użytkownika do dowolnej strony lub strony okna nadrzędnego, należy określić.  
  
-   "Przestawione" lub odłączyć od okno ramowe w osobnym oknie mini ramki, co użytkownik może go przenieść w odpowiednim miejscu.  
  
-   Można zmienić rozmiar podczas zmiennoprzecinkową.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [dokowanie i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md).  
  
##  <a name="_core_toolbars_and_tool_tips"></a>Paski narzędzi i etykietki narzędzi  
 Paski narzędzi MFC można również wyświetlić "etykietki narzędzi" — okna podręczne niewielki rozmiar zawierający krótki opis przeznaczenia przycisku paska narzędzi. Jako użytkownik przesuwa wskaźnik myszy nad przycisku paska narzędzi, okna narzędzia Porada pojawia się na ofertę wskazówkę. Aby uzyskać więcej informacji, zobacz artykuł [etykietki narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md).  
  
##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>Ctoolbar — i klasy CToolBarCtrl  
 Zarządzanie pasków narzędzi aplikacji za pomocą klasy [ctoolbar —](../mfc/reference/ctoolbar-class.md). Począwszy od wersji 4.0, MFC `CToolBar` zostały reimplemented korzystać z formantu wspólnego narzędzi dostępnych w systemie Windows 95 lub nowszego i systemu Windows NT w wersji 3.51 lub nowszej.  
  
 Ta ponowna implementacja powoduje mniejsza ilość kodu MFC dla pasków narzędzi, ponieważ sprawia, że MFC użyć obsługi systemu operacyjnego. Ponowna implementacja również poprawia możliwości. Można użyć `CToolBar` funkcji elementów członkowskich do manipulowania paski narzędzi, lub można uzyskać odwołania do odpowiadającego [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiekt i jego elementów członkowskich wywoływać funkcje pasków narzędzi i dodatkowe funkcje.  
  
> [!TIP]
>  Jeśli użytkownik zainwestowały silnie w starszej implementacji MFC `CToolBar`, że obsługa jest nadal dostępny. Zapoznaj się z artykułem [przy użyciu Your starych pasków narzędzi](../mfc/using-your-old-toolbars.md).  
  
 Zobacz też przykładowe ogólne MFC [DOCKTOOL](../visual-cpp-samples.md).  
  
##  <a name="_core_the_toolbar_bitmap"></a>Mapa bitowa paska narzędzi  
 Utworzone na raz, `CToolBar` obiektu tworzy obraz paska narzędzi przez ładowanie pojedynczego mapy bitowej zawierającego jeden obraz dla każdego przycisku. Kreator aplikacji tworzy mapę bitową standardowym pasku narzędzi, które można dostosować z programem Visual C++ [paska narzędzi edytora](../windows/toolbar-editor.md).  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Podstawowe informacje na temat narzędzi](../mfc/toolbar-fundamentals.md)  
  
-   [Zadokowane i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md)  
  
-   [Etykietki narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)  
  
-   [Praca z formantem paska narzędzi](../mfc/working-with-the-toolbar-control.md)  
  
-   [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)  
  
-   [Ctoolbar —](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) klas  
  
## <a name="see-also"></a>Zobacz też  
 [Paski narzędzi](../mfc/toolbars.md)   
 [Edytor paska narzędzi](../windows/toolbar-editor.md)

