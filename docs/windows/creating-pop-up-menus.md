---
title: Tworzenie menu wyskakujących | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- context menus, Menu Editor
- pop-up menus, creating
- menus, pop-up
- menus, creating
- shortcut menus, creating
- pop-up menus, displaying
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 878f7b31d98a26a76b8466e7a93cd3d165ed145f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583460"
---
# <a name="creating-pop-up-menus"></a>Tworzenie menu wyskakujących

[Menu wyskakujące](../mfc/menus-mfc.md) wyświetlania często używanych poleceń. Mogą to być kontekstowo lokalizacji wskaźnika. Używanie wyskakujących menu w aplikacji wymaga tworzenia samo menu, a następnie nawiąż połączenie z kodu aplikacji.

Po utworzeniu zasobu menu, kod aplikacji musi załadować zasobu menu i używać [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) aby spowodować, że są wyświetlane w menu. Po użytkownik został odrzucony menu podręcznego, klikając poza nim lub kliknie polecenie, że funkcja zwróci. Jeśli użytkownik wybierze polecenie, komunikat tego polecenia będą wysyłane do okna, w których uchwyt został przekazany.

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