---
title: Edytor okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors, Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes, editing
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 39c34487941ee45f91883ed91b1faa2c93973cfe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601727"
---
# <a name="dialog-editor"></a>Edytor okien dialogowych

**Okna dialogowego** Edytor umożliwia tworzenie i edytowanie zasobów okien dialogowych. Otwórz Edytor okien dialogowych przez dwukrotne kliknięcie pliku .rc okna dialogowego w **widok zasobów** okna (**widoku** > **widok zasobów**). Należy pamiętać, że **widok zasobów** nie jest dostępny w wersji Express.

Jednym z pierwszych kroków w tworzeniu nowego okna dialogowego (lub szablonu okna dialogowego) jest dodanie formantów do okna dialogowego. W **okna dialogowego** edytora, można rozmieścić formanty w celu dopasowania niektórych rozmiaru, kształtu lub wyrównania lub przenosić je około do pracy w oknie dialogowym. W łatwy sposób można również usunąć formant.

Okno dialogowe można przechowywać jako szablon w celu ponownego użycia. Można także łatwo przełączyć się między projektowaniem okna dialogowego a edycją kodu, który go implementuje.

Jest również możliwe edytowanie właściwości jednego lub wielu formantów w edytorze okien dialogowych. Możesz zmienić kolejność tabulacji, czyli kolejność, w której formanty uzyskują Skoncentruj się kiedy **kartę** naciśnięcia klawisza lub zdefiniować klawisza dostępu (kombinację klawiszy), który umożliwia użytkownikom na wybór formantu przy użyciu klawiatury. Aby uzyskać listę predefiniowanych klawiszy dostępu, zobacz [klucze akceleratora dla edytora okien dialogowych](../windows/accelerator-keys-for-the-dialog-editor.md).

**Okna dialogowego** Edytor umożliwia także używanie niestandardowych formantów, w tym formantów ActiveX. Ponadto można edytować [widok formularza](../mfc/reference/cformview-class.md), [widoków rekordów](../data/record-views-mfc-data-access.md), lub [paski dialogowe](../mfc/dialog-bars.md).

Począwszy od programu Visual Studio 2015, służy Edytor okien dialogowych do definiowania dynamicznych układy, które określają, jak formanty, przenoszenie i zmienianie rozmiaru, gdy użytkownik zmienia rozmiar okna dialogowego. Aby uzyskać więcej informacji, zobacz [układ dynamiczny](../mfc/dynamic-layout.md).

- [Tworzenie nowego okna dialogowego](../windows/creating-a-new-dialog-box.md)

- [Tworzenie okna dialogowego, którego nie można zamknąć w czasie wykonywania](../windows/creating-a-dialog-box-that-users-cannot-exit.md)

- [Pokazywanie i ukrywanie paska narzędzi Edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)

- [Przełączanie między edytorem okien dialogowych a kodem](../windows/switching-between-dialog-box-controls-and-code.md)

- [Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)

- [Dodawanie obsługi zdarzeń dla kontrolek okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md)

- [Testowanie okna dialogowego](../windows/testing-a-dialog-box.md)

- [Klucze akceleratora dla Edytora okien dialogowych](../windows/accelerator-keys-for-the-dialog-editor.md)

- [Rozwiązywanie problemów z Edytorem okien dialogowych](../windows/troubleshooting-the-dialog-editor.md)

   > [!TIP]
   > Podczas korzystania z **okna dialogowego** edytora w wielu przypadkach, kliknięcie prawym przyciskiem myszy wyświetli menu skrótów z najczęściej używanymi poleceniami.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)  
[Kontrolki](../mfc/controls-mfc.md)  
[Klasy kontrolek](../mfc/control-classes.md)  
[Klasy okien dialogowych](../mfc/dialog-box-classes.md)  
[Kontrolki okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)