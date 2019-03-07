---
title: Edytory zasobów (C++)
ms.date: 02/14/2019
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
ms.openlocfilehash: 461322076e2de4e2cd89c6d39592989aecc75361
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563020"
---
# <a name="resource-editors-c"></a>Edytory zasobów (C++)

Edytor zasobów to specjalne środowisko służące do tworzenia lub modyfikowania zasobów, które są zawarte w projekcie programu Visual Studio. Edytory zasobów programu Visual Studio udostępnianie techniki i interfejsy, które ułatwiają tworzenie i modyfikowanie zasobów aplikacji, szybkie i łatwe. Edytory zasobów umożliwia wyświetlanie i edytowanie zasobów w odpowiednich zasobach w edytorze i w wersji zapoznawczej.

Odpowiedniego edytora jest otwierany automatycznie podczas tworzenia lub otwierania zasobu.

> [!NOTE]
> Ponieważ projektów zarządzanych plików skryptu zasobu nie jest używany, należy otworzyć swoich zasobów przed **Eksploratora rozwiązań**. Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [Edytor plików binarnych](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

|Użyj...|Aby edytować...|
|----------------|----------------|
|[Edytor klawiszy skrótów](../windows/accelerator-editor.md)|Tabele akceleratora w projektach języka Visual C++.|
|[Edytor plików binarnych](binary-editor.md)|Dane binarne informacje i zasoby niestandardowe w projektach języka Visual C++, Visual Basic lub Visual C#.|
|[Edytor okien dialogowych](../windows/dialog-editor.md)|Okna dialogowe w projektach języka Visual C++.|
|[Edytor obrazów](../windows/image-editor-for-icons.md)|Mapy bitowe, ikony, kursorów i inne pliki obrazów w projektach języka Visual C++, Visual Basic lub Visual C#.|
|[Edytor menu](../windows/menu-editor.md)|Menu zasobów w projektach języka Visual C++.|
|[Edytor Ribbon](../mfc/ribbon-designer-mfc.md)|Zasoby wstążki w projektach MFC.|
|[Edytor ciągów](../windows/string-editor.md)|Ciąg tabel z projektów Visual C++.|
|[Edytor paska narzędzi](../windows/toolbar-editor.md)|Zasoby paska narzędzi z projektów Visual C++. **Edytor paska narzędzi** jest częścią **edytora obrazów**.|
|[Edytor informacji o wersji](../windows/version-information-editor.md)|Informacje o wersji w projektach języka Visual C++.|

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [jak: Tworzenie zasobów](../windows/how-to-create-a-resource-script-file.md).

## <a name="view-and-edit-resources"></a>Wyświetlanie i edytowanie zasobów

Każdy typ zasobu ma edytorze zasobów specyficznych dla typu zasobu. Można zmienić kolejność, zmiany rozmiaru, dodawać formanty i funkcje lub inny sposób modyfikować aspektów zasobu za pomocą edytora skojarzone. Można również edytować zasobu w [format tekstu](../windows/how-to-open-a-resource-script-file-in-text-format.md) i [format binarny](../windows/opening-a-resource-for-binary-editing.md).

Niektóre typy zasobów są pojedyncze pliki, które mogą być importowane i używane na różne sposoby; obejmują one map bitowych, ikon, kursorów, paski narzędzi i pliki html. Takie zasoby mają nazwy plików i [identyfikatory zasobów](../windows/symbols-resource-identifiers.md). Inne, takie jak okna dialogowe, menu i tabele ciągów w projektach systemu Win32, istnieje tylko jako część pliku skryptu (.rc) zasobów lub zasobu, plik szablonu (.rct).

Zasoby można również edytować poza projektem, bez konieczności otwarty projekt, zobacz [jak: Tworzenie zasobów](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Można modyfikować właściwości zasobu za pomocą **właściwości** okna.

- Aby edytować właściwości zasobu w [widok zasobów](/windows/how-to-create-a-resource-script-file#create-resources), kliknij prawym przyciskiem myszy zasób, o których chcesz edytować, a następnie wybierz **właściwości**.  Następnie w [okno właściwości](/visualstudio/ide/reference/properties-window), zmiana właściwości zasobu.

- Aby cofnąć zmiany wprowadzone do właściwości zasobu, upewnij się, zasób ma fokus w **widok zasobów** i wybierz polecenie **Cofnij** z **Edytuj** menu.

### <a name="win32-resources"></a>Zasoby Win32

Dostęp zasobów Win32 w [widok zasobów](/windows/how-to-create-a-resource-script-file#create-resources) okienka.

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Aby wyświetlić zasób Win32 w edytorze zasobów

1. Przejdź do menu **widoku** > **widok zasobów**.

1. Jeśli **widok zasobów** okno nie jest oknem najważniejsze wybierz **widok zasobów** kartę, aby przełączyć go do góry.

1. Z **widok zasobów**, rozwiń folder dla projektu, który zawiera zasoby, które chcesz wyświetlić. Na przykład, jeśli chcesz wyświetlić zasobu okna dialogowego, rozwiń **okna dialogowego** folderu.

1. Kliknij dwukrotnie zasób, na przykład **IDD_ABOUTBOX**.

   Zasób zostanie otwarty w edytorze odpowiednie. Na przykład dla zasobów okna dialogowego, zasobu otwiera wewnątrz **Edytor okien dialogowych**.

#### <a name="to-delete-an-existing-win32-resource"></a>Aby usunąć istniejący zasób Win32

1. W **widok zasobów**, rozwiń węzeł dla typu zasobu.

1. Kliknij prawym przyciskiem myszy do zasobu, które chcesz usunąć, a następnie wybierz **Usuń**.

> [!TIP]
> Tej metody można użyć również, gdy plik .rc jest otwarty w oknie dokumentu poza projektem.

### <a name="managed-project-resources"></a>Zasoby zarządzanego projektu

Ponieważ projektów zarządzanych, nie używaj plików skryptu zasobu, należy otworzyć swoich zasobów przed **Eksploratora rozwiązań**. Użyj [edytora obrazów](../windows/image-editor-for-icons.md) i [Edytor plików binarnych](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami i edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

- Aby wyświetlić zasobów zarządzanych w edytorze zasobów, w **Eksploratora rozwiązań**, kliknij dwukrotnie zasób, na przykład *Bitmap1.bmp*, i zasobu, który zostanie otwarty w edytorze odpowiednie.

- Do usuwania istniejących zasobów zarządzanych w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy zasób, o których chcesz usunąć, a następnie wybierz **Usuń**.

## <a name="preview-resources"></a>Zasoby (wersja zapoznawcza)

Zasobów, aby umożliwić wyświetlanie zasobów graficznych bez ich otwierania w wersji zapoznawczej. Podgląd jest również przydatne dla plików wykonywalnych po została skompilowana, ponieważ zmiany numery identyfikatorów zasobów. Ponieważ te identyfikatory numeryczne często nie zapewniają wystarczających informacji, wyświetlanie podglądu zasobów pomaga szybko określić ich.

Następujące typy zasobów zapewniają układ wizualizacji (wersja zapoznawcza): Mapa bitowa, okno dialogowe, ikony, Menu, kursor, pasek narzędzi

Poniższe zasoby nie przedstawiają wyświetlania podglądu: Akcelerator, informacje o wersji manifestu, Tabela ciągów

> [!NOTE]
> Aby wyświetlić podgląd zasobów wymaga systemu Win32.

### <a name="to-preview-resources"></a>Aby wyświetlić podgląd zasobów

1. W [widok zasobów](/windows/how-to-create-a-resource-script-file#create-resources) lub okno dokumentu, wybierz zasób, na przykład **IDD_ABOUTBOX**.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), wybierz opcję **stron właściwości** przycisku.

   > [!TIP]
   > Użyj skrótu, przejdź do menu **widoku** > **stron właściwości**.

   **Właściwość** zostanie otwarta strona dla zasobu, za pomocą wyświetlania podglądu tego zasobu. Możesz użyć **się** i **dół** klawiszy strzałek, aby przejść w drzewie w kontrolce **widok zasobów** lub okno dokumentu. **Właściwość** strona będzie pozostają otwarte i Pokaż dowolnego zasobu, który ma fokus i można je przeglądać.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Identyfikatory zasobów (symbole)](../windows/symbols-resource-identifiers.md)<br/>