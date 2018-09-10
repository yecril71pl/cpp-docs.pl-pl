---
title: Tworzenie menu wyskakujących (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3fd2fcc5fc8603f265fa2d213325227baecd7f5d
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313771"
---
# <a name="creating-pop-up-menus-c"></a>Tworzenie menu wyskakujących (C++)

[Menu wyskakujące](../mfc/menus-mfc.md) wyświetlania często używanych poleceń. Mogą to być kontekstowo lokalizacji wskaźnika. Używanie wyskakujących menu w aplikacji wymaga tworzenia samo menu, a następnie nawiąż połączenie z kodu aplikacji.

Po utworzeniu zasobu menu, kod aplikacji musi załadować zasobu menu i używać [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) aby spowodować, że są wyświetlane w menu. Po użytkownik został odrzucony menu podręcznego, klikając poza nim lub kliknie polecenie, że funkcja zwróci. Jeśli użytkownik wybierze polecenie, komunikat tego polecenia będą wysyłane do okna, w których uchwyt został przekazany.

### <a name="to-create-a-pop-up-menu"></a>Aby utworzyć menu podręcznego

1. [Tworzenie menu](../windows/creating-a-menu.md) z pustym tytułem (nie zapewniają **podpis**).

2. [Dodać polecenie menu do menu Nowy](../windows/adding-commands-to-a-menu.md). Przenieś do pierwszego polecenia menu poniżej tytułu menu puste (mówi tymczasowe podpis `Type Here`). Wpisz **podpis** i inne informacje.

   Powtórz ten proces dla innych poleceń menu w menu podręcznym.

3. Zapisz zasób menu.

   > [!TIP]
   > Aby uzyskać więcej informacji o wyświetlaniu menu podręcznego, zobacz [wyświetlanie jako Menu podręcznego](../windows/viewing-a-menu-as-a-pop-up-menu.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Łączenie menu wyskakującego z Twoją aplikacją](../windows/connecting-a-pop-up-menu-to-your-application.md)  
[Edytor menu](../windows/menu-editor.md)