---
title: Znalezienie zasobu ciągu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 308e84a84c39399c93d270ba4662b3b0f593e42d
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082491"
---
# <a name="finding-a-string-resource-c"></a>Znalezienie zasobu ciągu (C++)

Wyszukaj jeden lub więcej ciągów w tabeli ciągów i użyj [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) z **Znajdź w plikach** polecenia (**Edytuj** menu) aby znaleźć wszystkie wystąpienia ciągów które pasują do wzorca.

### <a name="to-find-a-string-in-the-string-table"></a>Aby znaleźć ciąg w tabeli ciągów

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Na **Edytuj** menu, kliknij przycisk **Znajdź i Zamień**, następnie wybierz **znaleźć**.

3. W **Znajdź** Wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz podpis tekst lub identyfikator zasobu ciągu ma zostać odnaleziona.

4. Wybierz dowolny z **znaleźć** opcje.

5. Kliknij przycisk **Znajdź następny**.

   > [!TIP]
   > Aby użyć wyrażeń regularnych podczas wyszukiwania plików, należy użyć **Znajdź w plikach** polecenia. Typ wyrażenia regularnego pasują do wzorca, lub kliknij przycisk po prawej stronie **Znajdź** pole, aby wyświetlić listę wyrażeń regularnych wyszukiwania. Po wybraniu wyrażenia z tej listy, zostanie zastąpiony jako wyszukiwany tekst w **Znajdź** pole. Upewnij się, jeśli używasz wyrażeń regularnych, **użycia: wyrażeń regularnych** pole wyboru jest zaznaczone.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, (te, których platformą docelową środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Instruktaż: Lokalizowanie interfejsów Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor ciągów](../windows/string-editor.md)  