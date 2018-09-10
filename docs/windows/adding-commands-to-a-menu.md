---
title: Dodawanie poleceń do Menu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.menu
dev_langs:
- C++
helpviewer_keywords:
- menu items, adding to menus
- menus [C++], adding items
- commands [C++], adding to menus
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2c67242195f54f543bdc8c0c1be49fbed69fe91
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318723"
---
# <a name="adding-commands-to-a-menu-c"></a>Dodawanie poleceń do Menu (C++)

### <a name="to-add-commands-to-a-menu"></a>Aby dodać polecenia do menu

1. [Tworzenie menu](../windows/creating-a-menu.md).

2. Na przykład kliknij nazwę menu **pliku**.

   Każde menu będzie Rozwiń i udostępnić pole nowego elementu w przypadku poleceń. Na przykład można dodać polecenia **New**, **Otwórz**, i **Zamknij** do **pliku** menu.

3. W polu Nowy element wpisz nazwę nowego polecenia menu.

   > [!NOTE]
   > Można wpisać tekst, który jest dostępny w **Menu** edytora i **podpis** pole w [okno właściwości](/visualstudio/ide/reference/properties-window). Można edytować właściwości nowego menu w jednej z tych lokalizacji.

   > [!TIP]
   > Można zdefiniować mnemoników klucza (klawisz dostępu), który umożliwia użytkownikowi wybranie polecenia menu. Wpisz znak (`&`) przed literę, aby określić, że mnemonik. Użytkownik może wybrać polecenie menu, wpisując tę literę.

4. W **właściwości** okna, wybierz opcję menu polecenie Właściwości, które są stosowane. Aby uzyskać więcej informacji, zobacz [właściwości poleceń Menu](../windows/menu-command-properties.md).

5. W **wiersza** pole w **właściwości** okna, wpisz ciąg monitu mają być wyświetlane na pasku stanu aplikacji.

   Spowoduje to utworzenie wpisu w tabeli ciągów za pomocą tego samego identyfikatora zasobu jako polecenia menu, który został utworzony.

   > [!NOTE]
   > Monity można stosować tylko do elementów menu za pomocą **okno podręczne** właściwość **True**. Na przykład elementy menu najwyższego poziomu może mieć monitów, jeśli mają one elementy menu podrzędne. Celem **monitu** jest wskazanie, co się stanie, jeśli użytkownik kliknie element menu.

6. Naciśnij klawisz **Enter** można ukończyć polecenia menu.

   Nowe pole elementu jest zaznaczone, aby można było utworzyć menu dodatkowych poleceń.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor menu](../windows/menu-editor.md)  