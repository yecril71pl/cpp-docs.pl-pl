---
title: Tworzenie ikony lub innego obrazu (Edytor obrazów dla ikon)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
ms.openlocfilehash: 45a119114c26513788b2cdc134e4258e42cf896d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503303"
---
# <a name="creating-an-icon-or-other-image-image-editor-for-icons"></a>Tworzenie ikony lub innego obrazu (Edytor obrazów dla ikon)

Możesz utworzyć nowy obraz (mapa bitowa, ikony, kursor lub narzędzi), a następnie użyć edytora obrazów w celu dostosowania jego wyglądu. Można również tworzyć nowe mapę bitową z deseniem po [szablonu](../windows/how-to-use-resource-templates.md).

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Aby dodać nowy zasób obrazu do niezarządzanego projektu C++

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Wstaw zasobów** z menu skrótów. (Jeśli masz już istniejący zasób obrazu w pliku .rc, takich jak kursora, użytkownik może po prostu kliknij prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora** z menu skrótów.)

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz typ zasobu obrazu, które chcesz utworzyć (**mapy bitowej**, na przykład) kliknięcie **New**.

   Jeśli znak plus (**+**) pojawia się obok typ zasobu obrazu w **Wstaw zasobów** okno dialogowe, oznacza to, narzędzi szablony są dostępne. Kliknij znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie kliknij przycisk **New**.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Aby dodać nowy zasób obrazu do projektu w języku programowania .NET

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder projektu (na przykład `WindowsApplication1`).

2. W menu skrótów kliknij **Dodaj**, następnie wybierz **Dodaj nowy element**.

3. W **kategorie** okienku rozwiń **lokalne elementy projektu** folderu, wybierz **zasobów**.

4. W **szablony** okienku, wybierz typ zasobu, czy chcesz dodać do projektu.

   Zasób jest dodawany do projektu w **Eksploratora rozwiązań** i zasobów zostanie otwarty w [edytora obrazów](../windows/image-editor-for-icons.md). Narzędzia dostępne w edytorze obrazu umożliwia teraz zmodyfikować obraz. Aby uzyskać więcej informacji na temat dodawania obrazów do projektów zarządzanych, zobacz [podczas ładowania obrazu w czasie projektowania](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

   > [!NOTE]
   > Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych. Aby uzyskać więcej informacji, zobacz [Creating Resource Files](/dotnet/framework/resources/creating-resource-files-for-desktop-apps) w *przewodniku dewelopera .NET Framework*.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[Konwertowanie map bitowych na paski narzędzi](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Tworzenie nowych pasków narzędzi](../windows/creating-new-toolbars.md)<br/>
[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)