---
title: Wyświetlanie i edytowanie zasobów w edytorze zasobów (C++)
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
ms.openlocfilehash: 02ab58d37f3f188c3d65740b218cb9b2ac799714
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742664"
---
# <a name="viewing-and-editing-resources-in-a-resource-editor-c"></a>Wyświetlanie i edytowanie zasobów w edytorze zasobów (C++)

Każdy typ zasobu ma **zasobów** edytora specyficznych dla typu zasobu. Można zmienić kolejność, zmiany rozmiaru, dodawać formanty i funkcje lub inny sposób modyfikować aspektów zasobu za pomocą edytora skojarzone. Można również edytować zasobu w [format tekstu](../windows/how-to-open-a-resource-script-file-in-text-format.md) i [format binarny](../windows/opening-a-resource-for-binary-editing.md).

Niektóre typy zasobów są pojedyncze pliki, które mogą być importowane i używane na różne sposoby; obejmują one map bitowych, ikon, kursorów, paski narzędzi i pliki html. Takie zasoby mają nazwy plików i [identyfikatory zasobów](../windows/symbols-resource-identifiers.md). Inne, takie jak okna dialogowe, menu i tabele ciągów w projektach systemu Win32, istnieje tylko jako część pliku skryptu (.rc) zasobów lub zasobu, plik szablonu (.rct).

> [!NOTE]
> Właściwości zasobu [można zmodyfikować w oknie właściwości](../windows/changing-the-properties-of-a-resource.md).

## <a name="win32-resources"></a>Zasoby Win32

Dostęp zasobów Win32 w [widok zasobów](../windows/resource-view-window.md) okienka.

### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Aby wyświetlić zasób Win32 w edytorze zasobów

1. Wybierz **widok zasobów** z **widoku** menu.

1. Jeśli **widok zasobów** okno nie jest oknem najważniejsze wybierz **widok zasobów** kartę, aby przełączyć go do góry.

1. Z **widok zasobów**, rozwiń folder dla projektu, który zawiera zasoby, które chcesz wyświetlić. Na przykład, jeśli chcesz wyświetlić zasobu okna dialogowego, rozwiń **okna dialogowego** folderu.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Kliknij dwukrotnie zasób, na przykład **IDD_ABOUTBOX**.

   Zasób zostanie otwarty w edytorze odpowiednie. Na przykład dla zasobów okna dialogowego, zasobu otwiera wewnątrz **okna dialogowego** edytora.

   Możesz również [wyświetlania zasobów w pliku .rc (skrypt zasobu) bez konieczności otwierania projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-delete-an-existing-win-32-resource"></a>Aby usunąć istniejący zasób Win 32

1. W **widok zasobów**, rozwiń węzeł dla typu zasobu.

2. Kliknij prawym przyciskiem myszy do zasobu, które chcesz usunąć, a następnie wybierz **Usuń** z menu skrótów.

   > [!NOTE]
   > Możesz usunąć zasób za pomocą tego samego polecenia w menu skrótów, gdy plik .rc jest otwarty w oknie dokumentu poza projektem.

## <a name="resources-in-managed-projects"></a>Zasoby w projektach zarządzanych

Ponieważ projektów zarządzanych, nie używaj plików skryptu zasobu, należy otworzyć swoich zasobów przed **Eksploratora rozwiązań**. Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>Aby wyświetlić zasobów zarządzanych w edytorze zasobów

W **Eksploratora rozwiązań**, kliknij dwukrotnie zasób, na przykład **Bitmap1.bmp**.

   Zasób zostanie otwarty w edytorze odpowiednie.

### <a name="to-delete-an-existing-managed-resource"></a>Aby usunąć istniejący zasób zarządzany

W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy zasób, o których chcesz usunąć, a następnie wybierz **Usuń** z menu skrótów.

## <a name="changing-the-properties-of-resources"></a>Zmiana właściwości zasobów

### <a name="to-edit-the-properties-of-a-resource"></a>Aby edytować właściwości zasobu

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy zasób, o których chcesz edytować, a następnie wybierz **właściwości** z menu skrótów.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), zmiana właściwości zasobu.

### <a name="to-undo-a-change-made-to-the-properties-of-a-resource"></a>Aby cofnąć zmiany wprowadzone do właściwości zasobu

1. Upewnij się, że zasób ma fokus w **widok zasobów**.

1. Wybierz **Cofnij** z **Edytuj** menu.

## <a name="previewing-resources"></a>Wyświetlanie podglądu zasobów

Zasobów, aby umożliwić wyświetlanie zasobów graficznych bez ich otwierania w wersji zapoznawczej. Podgląd jest również przydatne dla plików wykonywalnych, po ich skompilowany, ponieważ zmiany numery identyfikatorów zasobów. Ponieważ te identyfikatory numeryczne często nie zapewniają wystarczających informacji, wyświetlanie podglądu zasobów pomaga szybko określić ich.

Możesz wyświetlić podgląd wizualnym układem następujących zasobów:

- Mapy bitowej

- Okno dialogowe

- Ikona

- Menu

- Kursor

- Pasek narzędzi

Funkcja wyświetlania podglądu, nie ma zastosowania do zasobów akceleratora, Manifest, Tabela ciągów i informacje o wersji.

### <a name="to-preview-resources"></a>Aby wyświetlić podgląd zasobów

1. W [widok zasobów](../windows/resource-view-window.md) lub okno dokumentu, wybierz zasób, na przykład **IDD_ABOUTBOX**.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), wybierz opcję **stron właściwości** przycisku.

   \- lub —

   Na **widoku** menu, wybierz opcję **stron właściwości**.

   **Strona właściwości** zasobu zostanie otwarty w wersji zapoznawczej tego zasobu. Następnie można użyć **się** i **dół** klawiszy strzałek, aby przejść w drzewie w kontrolce **widok zasobów** lub okno dokumentu. **Strona właściwości** będzie pozostają otwarte i Pokaż dowolnego zasobu, który ma fokus i można je przeglądać.

> [!NOTE]
> Aby wyświetlić podgląd zasobów wymaga systemu Win32.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz także

[Instrukcje: otwieranie pliku skryptu zasobu spoza projektu (autonomicznego)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)