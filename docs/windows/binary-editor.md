---
title: Edytor plików binarnych (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.binary.F1
- vc.editors.binary
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
- binary data, editing
- resources [C++], opening for binary editing
- binary data
- hexadecimal bytes in binary data
- strings [C++], searching for
- file searches [C++]
- binary data, finding
- ASCII characters, finding in binary data
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 2a3ff3d89c809f57ea3ddbd70d5664fc8d13cec4
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320825"
---
# <a name="binary-editor-c"></a>Edytor plików binarnych (C++)

> [!WARNING]
> **Edytor plików binarnych** nie jest dostępny w wersji Express.

W edytorze binarnym służy do edytowania dowolnego zasobu w poziomie binarnym w formacie szesnastkowym lub w formacie ASCII. Można również użyć [znaleźć polecenia](/visualstudio/ide/reference/find-command) do wyszukiwania ciągów znaków ASCII lub bajty szesnastkowe. Należy używać **binarne** edytora tylko wtedy, gdy należy wyświetlić lub wprowadzić drobne zmiany zasoby niestandardowe lub typy zasobów, które nie są obsługiwane przez środowisko Visual Studio.

Aby otworzyć **Edytor plików binarnych**, należy najpierw wybrać **pliku** > **nowy** > **pliku** wybierz z menu głównego plik który chcesz edytować, a następnie wybierz strzałkę obok listy pola **Otwórz** przycisk, a następnie wybierz **Otwórz za pomocą** > **Edytor plików binarnych**.

> [!CAUTION]
> Edytowanie zasobów, takich jak okna dialogowe, obrazów lub menu w edytorze binarnym jest niebezpieczne. Niepoprawne edytowanie może spowodować uszkodzenie zasobów, dzięki czemu można odczytać w edytorze natywnych.

![Edytor plików binarnych](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
Dane binarne dla okna dialogowego wyświetlany w edytorze pliku binarnego

Tylko niektóre wartości ASCII są reprezentowane w edytorze binarnym (0x20 za pośrednictwem 0x7E). Rozszerzone znaki są wyświetlane jako okresy w sekcji wartość ASCII w edytorze binarnym (prawy panel). "Drukowalnych" znaki są wartości ASCII 32 za pośrednictwem 126.

> [!TIP]
> Podczas korzystania z **binarne** edytora w wielu przypadkach możesz kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów poleceń specyficznych dla zasobów. Dostępne polecenia zależą od tego, co kursor wskazuje. Na przykład jeśli klikniesz podczas wskazujący **binarne** Edytor przy użyciu wybranej wartości szesnastkowych, pokazuje, w menu skrótów **Wytnij**, **kopiowania**, i **wklejania**  poleceń.

## <a name="how-to"></a>Instrukcje

**Binarne** Edytor pozwala:

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Aby otworzyć zasób pulpitu Windows do edycji plików binarnych

1. W [widok zasobów](../windows/resource-view-window.md), wybierz plik określonego zasobu, który chcesz edytować.

1. Kliknij prawym przyciskiem myszy zasób, a następnie kliknij przycisk **otwartej obsługi danych binarnych** z menu skrótów.

   > [!NOTE]
   > Jeśli używasz [widok zasobów](../windows/resource-view-window.md) okna, aby otworzyć zasobu w formacie, że Visual Studio nie może rozpoznać (na przykład RCDATA lub zasobów niestandardowych), zasób zostanie automatycznie otwarty w **binarne** edytora.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>Aby otworzyć zarządzanych zasobów do edycji plików binarnych

1. W **Eksploratora rozwiązań**, wybierz plik określonego zasobu, który chcesz edytować.

1. Kliknij prawym przyciskiem myszy zasób, a następnie wybierz **Otwórz za pomocą** z menu skrótów.

1. W **Otwórz za pomocą** okna dialogowego wybierz **Edytor plików binarnych**.

   > [!NOTE]
   > Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

> [!NOTE]
> Jeśli chcesz używać **binarne** edytora w zasobie już poddane edycji w innym oknie edytora najpierw zamknąć pozostałe okna edytora.

### <a name="to-edit-a-resource"></a>Aby edytować zasobu

1. Wybierz bajtów, którą chcesz edytować.

   **Kartę** klucz przenosi fokus między szesnastkowym i sekcje ASCII **binarne** edytora. Możesz użyć **Page Up** i **Page Down** klucze przejście przez jeden ekran zasobów w danym momencie.

1. Wpisz nową wartość.

   Wartość natychmiast zmienia się w sekcjach ASCII i szesnastkowym i otrzymuje fokus do następnej wartości w wierszu.

   > [!NOTE]
   > **Binarne** edytora akceptuje automatycznie zmian, po zamknięciu edytora.

### <a name="to-find-binary-data"></a>Aby znaleźć dane binarne

Można wyszukiwać ciągi ASCII lub bajty szesnastkowe. Na przykład, aby wyszukać "Hello", należy można wyszukać dla dowolnego ciągu "Hello" lub "48 65 6C 6 C 6 f" (szesnastkowy).

1. Z **Edytuj** menu, wybierz [znaleźć](/visualstudio/ide/reference/find-command).

1. W **Znajdź** Wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub typu danych, którą chcesz znaleźć.

1. Wybierz dowolny z **znaleźć** opcje, a następnie wybierz **Znajdź następny**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Aby utworzyć nowy zasób niestandardowy lub danych

Można utworzyć nowy zasób niestandardowy lub danych, umieszczając w oddzielnym pliku przy użyciu składni pliku skryptu (.rc) normalny zasób, a następnie w tym pliku zasobu, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i klikając  **Obejmuje zasobów** w menu skrótów.

1. [Utwórz plik .rc](../windows/how-to-create-a-resource-script-file.md) zawierająca zasób niestandardowy lub danych.

   Niestandardowe dane można wpisać w pliku .rc, jako zakończony znakiem null cudzysłowie ciągi lub jako liczby całkowite w formacie dziesiętną, szesnastkowym lub ósemkowo.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik .rc projektu, a następnie kliknij przycisk **zasób zawiera** w menu skrótów.

1. W **dyrektywy czasu kompilacji** wpisz `#include` instrukcję, która zawiera nazwę pliku zawierającego niestandardowego zasobu. Na przykład:

    ```cpp
    #include mydata.rc
    ```

   Upewnij się, że składnia i pisownię możesz wpisać są poprawne. Zawartość **dyrektywy czasu kompilacji** pola są wstawiane do pliku skryptu zasobu, dokładnie tak, jak został wpisany.

1. Wybierz **OK** zapisaniu zmian.

Innym sposobem tworzenia niestandardowego zasobu jest do zaimportowania pliku zewnętrznego jako zasób niestandardowy. Aby uzyskać więcej informacji, zobacz [importowanie i eksportowanie zasobów](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> Tworzenie nowych zasobów niestandardowych lub danych wymaga systemu Win32.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)