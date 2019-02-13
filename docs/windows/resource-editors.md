---
title: Edytory zasobów (C++)
ms.date: 11/04/2016
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
ms.openlocfilehash: 43eab011cefed116723bd983b685c1c8c230326f
ms.sourcegitcommit: bec1480a03e7b4070b469a6c131a69f516bbac70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226322"
---
# <a name="resource-editors-c"></a>Edytory zasobów (C++)

A **zasobów** edytora to specjalne środowisko służące do tworzenia lub modyfikowania zasobów, które są zawarte w projekcie programu Visual Studio. Edytory zasobów programu Visual Studio udostępnianie techniki i interfejsy, które ułatwiają tworzenie i modyfikowanie zasobów aplikacji, szybkie i łatwe. Edytory zasobów umożliwia wyświetlanie i edytowanie zasobów w odpowiednich zasobach w edytorze i w wersji zapoznawczej.

Odpowiedniego edytora jest otwierany automatycznie podczas tworzenia lub otwierania zasobu.

> [!NOTE]
> Ponieważ projektów zarządzanych plików skryptu zasobu nie jest używany, należy otworzyć swoich zasobów przed **Eksploratora rozwiązań**. Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

|Użyj...|Aby edytować...|
|----------------|----------------|
|[Edytor klawiszy skrótów](../windows/accelerator-editor.md)|Tabele akceleratora w projektach języka Visual C++.|
|[Edytor plików binarnych](binary-editor.md)|Dane binarne informacje i zasoby niestandardowe w projektach języka Visual C++, Visual Basic lub Visual C#.|
|[Edytor okien dialogowych](../windows/dialog-editor.md)|Okna dialogowe w projektach języka Visual C++.|
|[Edytor obrazów](../windows/image-editor-for-icons.md)|Mapy bitowe, ikony, kursorów i inne pliki obrazów w projektach języka Visual C++, Visual Basic lub Visual C#.|
|[Edytor menu](../windows/menu-editor.md)|Menu zasobów w projektach języka Visual C++.|
|[Edytor Ribbon](../mfc/ribbon-designer-mfc.md)|Zasoby wstążki w projektach MFC.|
|[Edytor ciągów](../windows/string-editor.md)|Ciąg tabel z projektów Visual C++.|
|[Edytor paska narzędzi](../windows/toolbar-editor.md)|Zasoby paska narzędzi z projektów Visual C++. Edytor paska narzędzi jest częścią edytora obrazów.|
|[Edytor informacji o wersji](../windows/version-information-editor.md)|Informacje o wersji w projektach języka Visual C++.|

## <a name="view-and-edit-resources-in-a-resource-editor"></a>Wyświetlanie i edytowanie zasobów w edytorze zasobów

Każdy typ zasobu ma **zasobów** edytora specyficznych dla typu zasobu. Można zmienić kolejność, zmiany rozmiaru, dodawać formanty i funkcje lub inny sposób modyfikować aspektów zasobu za pomocą edytora skojarzone. Można również edytować zasobu w [format tekstu](../windows/how-to-open-a-resource-script-file-in-text-format.md) i [format binarny](../windows/opening-a-resource-for-binary-editing.md).

Niektóre typy zasobów są pojedyncze pliki, które mogą być importowane i używane na różne sposoby; obejmują one map bitowych, ikon, kursorów, paski narzędzi i pliki html. Takie zasoby mają nazwy plików i [identyfikatory zasobów](../windows/symbols-resource-identifiers.md). Inne, takie jak okna dialogowe, menu i tabele ciągów w projektach systemu Win32, istnieje tylko jako część pliku skryptu (.rc) zasobów lub zasobu, plik szablonu (.rct).

Zasoby można również edytować poza projektem, zobacz [jak: Otwieranie pliku skryptu zasobu spoza projektu (autonomicznego)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Właściwości zasobu [można zmodyfikować w oknie właściwości](../windows/changing-the-properties-of-a-resource.md).

Aby edytować właściwości zasobu:

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy zasób, o których chcesz edytować, a następnie wybierz **właściwości** z menu skrótów.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), zmiana właściwości zasobu.

Aby cofnąć zmiany wprowadzone do właściwości zasobu:

1. Upewnij się, że zasób ma fokus w **widok zasobów**.

1. Wybierz **Cofnij** z **Edytuj** menu.

### <a name="win32-resources"></a>Zasoby Win32

Dostęp zasobów Win32 w [widok zasobów](../windows/resource-view-window.md) okienka.

Aby wyświetlić zasób Win32 w edytorze zasobów:

1. Wybierz **widok zasobów** z **widoku** menu.

1. Jeśli **widok zasobów** okno nie jest oknem najważniejsze wybierz **widok zasobów** kartę, aby przełączyć go do góry.

1. Z **widok zasobów**, rozwiń folder dla projektu, który zawiera zasoby, które chcesz wyświetlić. Na przykład, jeśli chcesz wyświetlić zasobu okna dialogowego, rozwiń **okna dialogowego** folderu.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Kliknij dwukrotnie zasób, na przykład **IDD_ABOUTBOX**.

   Zasób zostanie otwarty w edytorze odpowiednie. Na przykład dla zasobów okna dialogowego, zasobu otwiera wewnątrz **okna dialogowego** edytora.

   Możesz również [wyświetlania zasobów w pliku .rc (skrypt zasobu) bez konieczności otwierania projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

Aby usunąć istniejący zasób Win 32:

1. W **widok zasobów**, rozwiń węzeł dla typu zasobu.

2. Kliknij prawym przyciskiem myszy do zasobu, które chcesz usunąć, a następnie wybierz **Usuń** z menu skrótów.

   > [!NOTE]
   > Możesz usunąć zasób za pomocą tego samego polecenia w menu skrótów, gdy plik .rc jest otwarty w oknie dokumentu poza projektem.

### <a name="resources-in-managed-projects"></a>Zasoby w projektach zarządzanych

Ponieważ projektów zarządzanych, nie używaj plików skryptu zasobu, należy otworzyć swoich zasobów przed **Eksploratora rozwiązań**. Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Aby wyświetlić zasobów zarządzanych w edytorze zasobów:

W **Eksploratora rozwiązań**, kliknij dwukrotnie zasób, na przykład *Bitmap1.bmp*.

   Zasób zostanie otwarty w edytorze odpowiednie.

Aby usunąć istniejącego zasobu zarządzanego:

W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy zasób, o których chcesz usunąć, a następnie wybierz **Usuń** z menu skrótów.

## <a name="preview-resources"></a>Zasoby (wersja zapoznawcza)

Zasobów, aby umożliwić wyświetlanie zasobów graficznych bez ich otwierania w wersji zapoznawczej. Podgląd jest również przydatne dla plików wykonywalnych, po ich skompilowany, ponieważ zmiany numery identyfikatorów zasobów. Ponieważ te identyfikatory numeryczne często nie zapewniają wystarczających informacji, wyświetlanie podglądu zasobów pomaga szybko określić ich.

Możesz wyświetlić podgląd wizualnym układem następujących zasobów: Mapa bitowa, okno dialogowe, ikony, Menu, kursor, pasek narzędzi

Funkcja wyświetlania podglądu, nie ma zastosowania do zasobów: Akcelerator, Manifest, Tabela ciągów i informacje o wersji

> [!NOTE]
> Aby wyświetlić podgląd zasobów wymaga systemu Win32.

Aby wyświetlić podgląd zasobów:

1. W [widok zasobów](../windows/resource-view-window.md) lub okno dokumentu, wybierz zasób, na przykład `IDD_ABOUTBOX`.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), wybierz opcję **stron właściwości** przycisku.

   > [!TIP]
   > W przypadku skrótu na **widoku** menu, wybierz opcję **stron właściwości**.

   **Strona właściwości** zasobu zostanie otwarty w wersji zapoznawczej tego zasobu. Następnie można użyć **się** i **dół** klawiszy strzałek, aby przejść w drzewie w kontrolce **widok zasobów** lub okno dokumentu. **Strona właściwości** będzie pozostają otwarte i Pokaż dowolnego zasobu, który ma fokus i można je przeglądać.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz także

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)<br/>
[Menu i inne zasoby](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)