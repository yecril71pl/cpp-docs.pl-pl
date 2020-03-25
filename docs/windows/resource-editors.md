---
title: Edytory zasobówC++()
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
ms.openlocfilehash: 5f12b126db7c0e040f06640d3ecd201007d73968
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167891"
---
# <a name="resource-editors-c"></a>Edytory zasobówC++()

Edytor zasobów to wyspecjalizowane środowisko do tworzenia lub modyfikowania zasobów uwzględnionych w projekcie programu Visual Studio. Edytory zasobów programu Visual Studio udostępniają techniki i interfejsy ułatwiające szybkie i łatwe tworzenie i modyfikowanie zasobów aplikacji. Edytory zasobów umożliwiają wyświetlanie i edytowanie zasobów w odpowiednim edytorze i Podgląd zasobów.

Odpowiedni edytor zostanie otwarty automatycznie podczas tworzenia lub otwierania zasobu.

> [!NOTE]
> Ponieważ projekty zarządzane nie używają plików skryptów zasobów, należy otworzyć zasoby z **Eksplorator rozwiązań**. Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [edytora binarnego](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

|Korzystanie z...|Aby edytować...|
|----------------|----------------|
|[Edytor klawiszy skrótów](../windows/accelerator-editor.md)|Tabele akceleratora w projektach C++ programu Visual Studio.|
|[Edytor plików binarnych](binary-editor.md)|Informacje o danych binarnych i zasoby niestandardowe C++w wizualizacjach, Visual Basic C# lub projektach wizualnych.|
|[Edytor okien dialogowych](../windows/dialog-editor.md)|Okna dialogowe w projektach programu C++ Visual Studio.|
|[Edytor obrazów](../windows/image-editor-for-icons.md)|Mapy bitowe, ikony, kursory i inne pliki obrazów w wizualizacji C++, Visual Basic lub Visual C# .|
|[Edytor menu](../windows/menu-editor.md)|Zasoby menu w projektach programu C++ Visual Studio.|
|[Edytor wstążki](../mfc/ribbon-designer-mfc.md)|Zasoby wstążki w projektach MFC.|
|[Edytor ciągów](../windows/string-editor.md)|Tabele ciągów w projektach programu C++ Visual Studio.|
|[Edytor paska narzędzi](../windows/toolbar-editor.md)|Zasoby paska narzędzi w projektach C++ programu Visual Studio. **Edytor paska narzędzi** jest częścią **edytora obrazu**.|
|[Edytor informacji o wersji](../windows/version-information-editor.md)|Informacje o wersji w projektach C++ programu Visual Studio.|

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku. RC, zobacz [How to: Create Resources](../windows/how-to-create-a-resource-script-file.md).

## <a name="view-and-edit-resources"></a>Wyświetlanie i edytowanie zasobów

Każdy typ zasobu ma Edytor zasobów specyficzny dla tego typu zasobu. Można zmieniać rozmieszczenie, zmieniać rozmiar, dodawać kontrolki i funkcje albo modyfikować aspekty zasobu przy użyciu skojarzonego z nim edytora. Możesz również edytować zasób w [formacie tekstowym](../windows/how-to-open-a-resource-script-file-in-text-format.md) i [formacie binarnym](../windows/opening-a-resource-for-binary-editing.md).

Niektóre typy zasobów są pojedynczymi plikami, które mogą być importowane i używane na różne sposoby. obejmują one mapy bitowe, ikony, kursory, paski narzędzi i pliki HTML. Takie zasoby mają nazwy plików i [identyfikatory zasobów](../windows/symbols-resource-identifiers.md). Inne, takie jak okna dialogowe, menu i tabele ciągów w projektach Win32, istnieją tylko jako część pliku skryptu zasobu (. RC) lub plik szablonu zasobów (. rct).

Zasoby mogą być również edytowane poza projektem bez otwartego projektu, zobacz [How to: Create Resources](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Właściwości zasobu można zmodyfikować przy użyciu okna **Właściwości** .

- Aby edytować właściwości zasobu, w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)kliknij prawym przyciskiem myszy zasób, który chcesz edytować, a następnie wybierz polecenie **Właściwości**.  Następnie w [okno właściwości](/visualstudio/ide/reference/properties-window)zmienić właściwości zasobu.

- Aby cofnąć zmiany wprowadzone we właściwościach zasobu, upewnij się, że zasób ma fokus w **Widok zasobów** i wybierz polecenie **Cofnij** z menu **Edycja** .

### <a name="win32-resources"></a>Zasoby Win32

Dostęp do zasobów Win32 można uzyskać w okienku [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources) .

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Aby wyświetlić zasób Win32 w edytorze zasobów

1. Przejdź do **widoku** menu, > inne > **Widok zasobów** **systemu Windows** .

1. Jeśli okno **Widok zasobów** nie jest oknem najwyższego poziomu, wybierz kartę **Widok zasobów** , aby ją wyświetlić.

1. W **Widok zasobów**rozwiń folder dla projektu zawierającego zasoby, które chcesz wyświetlić. Jeśli na przykład chcesz wyświetlić zasób okna dialogowego, rozwiń folder **okna dialogowego** .

1. Kliknij dwukrotnie zasób, na przykład **IDD_ABOUTBOX**.

   Zasób zostanie otwarty w odpowiednim edytorze. Na przykład dla zasobów okna dialogowego zasób zostanie otwarty w **edytorze okien dialogowych**.

#### <a name="to-delete-an-existing-win32-resource"></a>Aby usunąć istniejący zasób Win32

1. W **Widok zasobów**rozwiń węzeł dla typu zasobu.

1. Kliknij prawym przyciskiem myszy zasób, który chcesz usunąć, a następnie wybierz polecenie **Usuń**.

> [!TIP]
> Tej metody można również użyć, gdy plik. RC jest otwarty w oknie dokumentu poza projektem.

### <a name="managed-project-resources"></a>Zarządzane zasoby projektu

Ponieważ projekty zarządzane nie używają plików skryptów zasobów, należy otworzyć zasoby z **Eksplorator rozwiązań**. Użyj [edytora obrazów](../windows/image-editor-for-icons.md) i [edytora binarnego](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszystkie zarządzane zasoby, które chcesz edytować, muszą być zasobami połączonymi i edytorami zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

- Aby wyświetlić zasób zarządzany w edytorze zasobów, w **Eksplorator rozwiązań**kliknij dwukrotnie zasób, na przykład *BITMAP1. bmp*, a zasób zostanie otwarty w odpowiednim edytorze.

- Aby usunąć istniejący zasób zarządzany, w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy zasób, który chcesz usunąć, a następnie wybierz polecenie **Usuń**.

## <a name="preview-resources"></a>Podgląd zasobów

Wyświetl podgląd zasobów, aby umożliwić wyświetlanie zasobów graficznych bez ich otwierania. Podgląd jest również przydatny dla plików wykonywalnych po ich skompilowaniu, ponieważ identyfikatory zasobów zmieniają się na liczby. Ponieważ te identyfikatory liczbowe często nie zapewniają wystarczającej ilości informacji, Podgląd zasobów ułatwia ich szybkie identyfikowanie.

Następujące typy zasobów udostępniają podgląd układu wizualizacji: Mapa bitowa, okno dialogowe, ikona, menu, kursor, pasek narzędzi

Następujące zasoby nie udostępniają wizualizacji Visual Preview: akcelerator, manifest, tabela ciągów, informacje o wersji

> [!NOTE]
> Aby uzyskać podgląd zasobów, wymagany jest system Win32.

### <a name="to-preview-resources"></a>Aby wyświetlić podgląd zasobów

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources) lub oknie dokumentu wybierz zasób, na przykład **IDD_ABOUTBOX**.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window)wybierz przycisk **strony właściwości** .

   > [!TIP]
   > Użyj skrótu, przejdź do **widoku** menu, > **strony właściwości**.

   Zostanie otwarta strona **Właściwości** zasobu wyświetlająca podgląd tego zasobu. Możesz użyć klawiszy strzałek w **górę** i **w dół** , aby nawigować po formancie drzewa w **Widok zasobów** lub oknie dokumentu. Na stronie **Właściwości** pozostanie otwarta i zostanie wyświetlony dowolny zasób, który ma fokus i będzie można go wyświetlić.

## <a name="requirements"></a>Wymagania

None

## <a name="see-also"></a>Zobacz też

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Identyfikatory zasobów (symbole)](../windows/symbols-resource-identifiers.md)<br/>
