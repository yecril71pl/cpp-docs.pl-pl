---
title: Tworzenie okna dialogowego (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 928432000fb9a6347433b78b224e15f07ce810d2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742651"
---
# <a name="creating-a-dialog-box-c"></a>Tworzenie okna dialogowego (C++)

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-new-dialog-box"></a>Aby utworzyć nowe okno dialogowe

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Dodaj zasób** z menu skrótów.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W **Dodaj zasób** okno dialogowe, wybierz opcję **okna dialogowego** w **typ zasobu** , a następnie wybierz **New**.

   Jeśli znak plus (**+**) pojawia się obok **okna dialogowego** typ zasobu, oznacza to dostępnych szablonów okno dialogowe. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie wybierz **New**.

   Zostanie otwarte nowe okno dialogowe w **okna dialogowego** edytora.

   Możesz również [otwarcie istniejącego okna dialogowe w edytorze okno dialogowe edycji](../windows/viewing-and-editing-resources-in-a-resource-editor.md).

## <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Aby utworzyć okno dialogowe, które użytkownik nie może zamknąć

Można utworzyć użytkownika nie może zamknąć okno dialogowe z środowiska uruchomieniowego. Tego rodzaju okno dialogowe jest użyteczny ze względu na potrzeby logowania oraz dla aplikacji lub blokady dokumentu.

1. W **właściwości** okienku okna dialogowego, ustaw **Menu systemowe** właściwości **false**.

   To ustawienie wyłącza menu systemu okna dialogowego i **Zamknij** przycisku.

1. W formularzu okno dialogowe Usuń **anulować** i **OK** przycisków.

   W czasie wykonywania użytkownik nie może zamknąć okno modalne okno dialogowe, które ma te cechy.

Umożliwia testowanie tego rodzaju okno dialogowe funkcji okno dialogowe testowej wykrywa, gdy **Esc** naciśnięciu. (**Esc** jest również nazywany vk_escape — klawisz wirtualnego.) Niezależnie od tego, jak okno dialogowe umożliwia zachowanie w czasie wykonywania, możesz zakończyć tryb testowy, naciskając klawisz **Esc**.

> [!NOTE]
> Dla aplikacji MFC, aby utworzyć okno dialogowe, którego nie można zamknąć, należy zastąpić domyślne zachowanie `OnOK` i `OnCancel` ponieważ nawet wtedy, gdy usuniesz skojarzone przyciski, nadal można odrzucić okno dialogowe, naciskając klawisz  **Wprowadź** lub **Esc**.

Aby uzyskać informacje dotyczące sposobu dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Instrukcje: tworzenie zasobu](../windows/how-to-create-a-resource.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)