---
title: Przenoszenie oraz kopiowanie menu i poleceń Menu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands, copying on menus
- menu items, moving
- commands, moving on menus
- menu items, copying
ms.assetid: 1d8df535-9922-4579-a9c2-37aeac1856eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc95eef2c3cca678ae291846c2ebe0e5c1e80997
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609085"
---
# <a name="moving-and-copying-menus-and-menu-commands"></a>Przenoszenie oraz kopiowanie menu i poleceń menu

Można przenosić i kopiować, menu i poleceń menu przy użyciu metody przeciągania i upuszczania lub za pomocą poleceń w menu skrótów (kliknij prawym przyciskiem myszy menu).

### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Do przeniesienia lub skopiowania menu lub poleceń menu przy użyciu metody przeciągania i upuszczania

1. Przeciągnij lub skopiuj element, który chcesz przenieść do:

   - Nowa lokalizacja bieżącego menu.

   - Inne menu. (Można przejść do innych menu, przeciągając wskaźnik myszy nad nimi.)

2. Pomijać polecenia menu, gdy prowadnicę wstawiania pokazuje pozycji, które chcesz.

### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Do przeniesienia lub skopiowania menu lub poleceń za pomocą polecenia menu skrótów

1. Kliknij prawym przyciskiem myszy jednego lub kilku menu lub poleceń menu.

2. Z menu skrótów wybierz polecenie **Wytnij** (Aby przenieść) lub **kopiowania**.

3. Jeśli przenosisz elementy do menu inny zasób lub pliku skryptu zasobu, [otwórz go w innym oknie](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

4. Wybierz pozycję menu lub polecenia menu, który chcesz przenieść lub skopiować do.

5. Z menu skrótów wybierz polecenie **Wklej**. Element przenoszone lub kopiowane jest umieszczany przed elementem, którą wybierzesz.

   > [!NOTE]
   > Można również przeciągnąć, skopiuj i Wklej do innych menu w innych oknach menu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Instrukcje dotyczące ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości i [Instruktaż: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor menu](../windows/menu-editor.md)