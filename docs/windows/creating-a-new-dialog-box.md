---
title: Tworzenie nowego okna dialogowego (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 285444b5f9bfa29ab00fc6a2ca1b644208bc95a8
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315798"
---
# <a name="creating-a-new-dialog-box-c"></a>Tworzenie nowego okna dialogowego (C++)

### <a name="to-create-a-new-dialog-box"></a>Aby utworzyć nowe okno dialogowe

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Dodaj zasób** z menu skrótów.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. W **Dodaj zasób** okno dialogowe, wybierz opcję **okna dialogowego** w **typ zasobu** , a następnie kliknij przycisk **New**.

   Jeśli znak plus (**+**) pojawia się obok **okna dialogowego** typ zasobu, oznacza to dostępnych szablonów okno dialogowe. Kliknij znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie kliknij przycisk **New**.

   Zostanie otwarte nowe okno dialogowe w **okna dialogowego** edytora.

   Możesz również [otwarcie istniejącego okna dialogowe w edytorze okno dialogowe edycji](../windows/viewing-and-editing-resources-in-a-resource-editor.md).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Instrukcje: tworzenie zasobu](../windows/how-to-create-a-resource.md)  
[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytor okien dialogowych](../windows/dialog-editor.md)