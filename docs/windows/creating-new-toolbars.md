---
title: Tworzenie nowych pasków narzędzi (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- toolbars [C++], creating
- Toolbar editor [C++], creating new toolbars
- Insert Resource
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
ms.openlocfilehash: 3c36579560c78ff77a624e4827df9d6a9302ae57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551310"
---
# <a name="creating-new-toolbars-c"></a>Tworzenie nowych pasków narzędzi (C++)

### <a name="to-create-a-new-toolbar"></a>Aby utworzyć nowy pasek narzędzi

1. W **zasobów** wyświetlić, kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Dodaj zasób** z menu skrótów. (Jeśli masz istniejący pasek narzędzi w pliku .rc, użytkownik może po prostu kliknij prawym przyciskiem myszy **narzędzi** i wybierz polecenie **Wstaw narzędzi** z menu skrótów.)

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. W **Dodaj zasób** okno dialogowe, wybierz opcję **narzędzi** w **typ zasobu** , a następnie kliknij przycisk **New**.

   Jeśli znak plus (**+**) pojawia się obok **narzędzi** typ zasobu oznacza że narzędzi szablony są dostępne. Kliknij znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie kliknij przycisk **New**.

   \- lub —

3. [Konwertowanie istniejącej mapy bitowej na pasku narzędzi](../windows/converting-bitmaps-to-toolbars.md).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

ATL i MFC

## <a name="see-also"></a>Zobacz też

[Edytor paska narzędzi](../windows/toolbar-editor.md)