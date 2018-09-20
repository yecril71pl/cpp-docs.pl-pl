---
title: Grupy z kartami MDI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35113181a21a5ff265b12269f57ee853f6011abc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442165"
---
# <a name="mdi-tabbed-groups"></a>Grupy z kartami MDI

Wiele funkcji grupy z kartami interfejsu (MDI) dokumentu umożliwia wielu aplikacji interfejsu (MDI) dokumentu do wyświetlenia jednego lub kilku okien z kartami (lub grupy z kartami systemu Windows, znane jako *grupy z kartami*) w obszarze klienta MDI. W pionie lub w poziomie można wyrównać okien z zakładkami. Jeśli aplikacja obsługuje więcej niż jednej grupy z kartami MDI, grupy są oddzielone rozdzielaczy.

## <a name="features"></a>Funkcje

Poniżej przedstawiono funkcje grup z kartami MDI:

- Aplikacja można dynamicznie utworzyć okien z zakładkami.

- Aplikację można wyrównać okien z zakładkami, poziomo czy pionowo.

- Grupy z kartami systemu Windows są oddzielone rozdzielaczy. Użytkownika można zmienić rozmiar grupy z kartami za pomocą rozdzielacza.

- Użytkownik może przeciągać poszczególnych kart między grupami.

- Użytkownik może przeciągać poszczególnych kart, aby tworzyć nowe grupy.

- Użytkownik może przenieść karty lub tworzyć nowe grupy za pomocą menu skrótów.

- Aplikację można zapisać i załadować układu okien z zakładkami.

- Aplikację można zapisać i załadować listy dokumentów MDI.

- Aplikację można uzyskać dostępu do poszczególnych grup z kartami i modyfikować ich parametrów.

### <a name="using-mdi-tabbed-groups"></a>Za pomocą MDI grupy z kartami

Do zadań wykonywanych za pomocą grup z kartami MDI są następujące:

- Aby włączyć grupy z kartami MDI dla okna głównej ramki, należy wywołać [CMDIFrameWndEx::EnableMDITabbedGroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups). Drugi parametr tej metody jest wystąpieniem `CMDITabInfo` klasy. Można używać parametrów domyślnych lub zmodyfikuj je przed wywołaniem `CMDIFrameWndEx::EnableMDITabbedGroups`.

- Aby zmodyfikować właściwości grupy z kartami MDI w czasie wykonywania, należy utworzyć lub zmodyfikować `CMDITabInfo` obiektu, a następnie wywołać `CMDIFrameWndEx::EnableMDITabbedGroups` ponownie

- Aby uzyskać listę MDI z kartami systemu windows, wywołania `CMDIFrameWndEx::GetMDITabGroups`.

- Aby utworzyć nową grupę z kartami MDI obok aktywnej grupy z kartami, wywołaj `CMDIFrameWndEx::MDITabNewGroup`.

- Aby przenieść fokus wprowadzania do poprzedniego lub następnego okna grupy z kartami, należy wywołać `CMDIFrameWndEx::MDITabMoveToNextGroup`.

- Ustalenie, czy okno jest elementem członkowskim MDI z kartami wywołanie grupy `CMDIFrameWndEx::IsMemberOfMDITabGroup`.

- Aby ustalić, czy kart MDI lub grupy z kartami MDI są włączone dla okna głównej ramki, należy wywołać `CMDIFrameWndEx::AreMDITabs`. Aby tylko należy określić, czy włączono wybór grup z kartami MDI, należy wywołać `CMDIFrameWndEx::IsMDITabbedGroup`.

- Aby wyświetlić menu skrótów, gdy użytkownik kliknie kartę lub przeciąganie go do innej grupy z kartami MDI, Zastąp `CMDIFrameWndEx::OnShowMDITabContextMenu` w `CMDIFrameWndEx`-klasy pochodnej. Jeśli ta metoda nie jest zaimplementowane, aplikacja nie wyświetli menu skrótów.

- Aby zapisać układ grup z kartami MDI w aplikacji, należy wywołać `CMDIFrameWndEx::SaveMDIState`. Można załadować uprzednio zapisanego MDI z kartami profilu grupy, wywołaj `CMDIFrameWndEx::LoadMDIState`. Można również wywołać tych metod do załadowania lub zapisania listy otwartych dokumentów w aplikacji MDI. Aby uzyskać więcej informacji na temat zapisywanie i ładowanie stanu MDI, zobacz [CMDIFrameWndEx::LoadMDIState](../mfc/reference/cmdiframewndex-class.md#loadmdistate).

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Klasa CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md)<br/>
[Klasa CMDIChildWndEx](../mfc/reference/cmdichildwndex-class.md)<br/>
[Klasa CMDITabInfo](../mfc/reference/cmditabinfo-class.md)
