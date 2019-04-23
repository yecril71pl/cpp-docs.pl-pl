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
ms.openlocfilehash: 832dbf711307b81527bcaff0d1e1b8138f208e46
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040387"
---
# <a name="binary-editor-c"></a>Edytor plików binarnych (C++)

> [!CAUTION]
> Edytowanie zasobów, takich jak okna dialogowe, obrazów lub menu w **Edytor plików binarnych** jest niebezpieczne. Niepoprawne edytowanie może spowodować uszkodzenie zasobów, dzięki czemu można odczytać w edytorze natywnych.

**Edytor plików binarnych** służy do edytowania dowolnego zasobu w poziomie binarnym w formacie szesnastkowym lub w formacie ASCII. Można również użyć [znaleźć polecenia](/visualstudio/ide/reference/find-command) do wyszukiwania ciągów znaków ASCII lub bajty szesnastkowe. Użyj **Edytor plików binarnych** tylko potrzebne do wyświetlania lub wprowadzić drobne zmiany zasoby niestandardowe lub typy zasobów, które nie są obsługiwane przez środowisko Visual Studio. **Edytor plików binarnych** nie jest dostępny w wersji Express.

- Aby otworzyć **Edytor plików binarnych** dla nowego pliku, przejdź do menu **pliku** > **New** > **pliku**, wybierz typ plik który chcesz edytować, a następnie wybierz strzałkę obok listy pola **Otwórz** przycisk, a następnie wybierz **Otwórz za pomocą** > **Edytor plików binarnych**.

- Aby otworzyć **Edytor plików binarnych** na istniejący plik, przejdź do menu **pliku** > **Otwórz** > **pliku**, wybierz opcję plik który chcesz edytować, a następnie wybierz strzałkę obok listy pola **Otwórz** przycisk, a następnie wybierz **Otwórz za pomocą** > **Edytor plików binarnych**.

   ![Edytor plików binarnych](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   Dane binarne dla okna dialogowego wyświetlane w **Edytor plików binarnych**

Tylko niektóre wartości ASCII są reprezentowane w **Edytor plików binarnych** (0x20 za pośrednictwem 0x7E). Rozszerzone znaki są wyświetlane jako kropek w prawym okienku ASCII wartość sekcji **Edytor plików binarnych**. Drukowalnych znaków są wartości ASCII 32 za pośrednictwem 126.

> [!TIP]
> Podczas korzystania z **Edytor plików binarnych**, w wielu przypadkach możesz kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów poleceń specyficznych dla zasobów. Dostępne polecenia zależą od tego, co kursor wskazuje. Przykładowo po kliknięciu prawym przyciskiem myszy podczas wskazujący **Edytor plików binarnych** przy użyciu wybranej wartości szesnastkowych, w menu skrótów pojawia się **Wytnij**, **kopiowania**i **Wklej** poleceń.

## <a name="how-to"></a>Instrukcje

**Edytor plików binarnych** umożliwia:

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Aby otworzyć zasób pulpitu Windows do edycji plików binarnych

1. W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), wybierz plik określonego zasobu, który chcesz edytować.

1. Kliknij prawym przyciskiem myszy zasób, a następnie wybierz pozycję **otwartej obsługi danych binarnych**.

> [!NOTE]
> Jeśli używasz **widok zasobów** okna, aby otworzyć zasobu w formacie, który nie rozpoznaje programu Visual Studio, takie jak RCDATA lub zasobów niestandardowych zasobów jest automatycznie otwierany w **Edytor plików binarnych**.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>Aby otworzyć zarządzanych zasobów do edycji plików binarnych

1. W **Eksploratora rozwiązań**, wybierz plik określonego zasobu, który chcesz edytować.

1. Kliknij prawym przyciskiem myszy zasób, a następnie wybierz pozycję **Otwórz za pomocą**.

1. W **Otwórz za pomocą** okna dialogowego wybierz **Edytor plików binarnych**.

> [!NOTE]
> Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i **Edytor plików binarnych** do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

### <a name="to-edit-a-resource"></a>Aby edytować zasobu

Jeśli chcesz używać **Edytor plików binarnych** w zasobie już poddane edycji w innym oknie edytora, zamknąć pozostałe okna edytora najpierw.

1. Wybierz bajtów, którą chcesz edytować.

   **Kartę** klucz przenosi fokus między szesnastkowym i sekcje ASCII **Edytor plików binarnych**. Możesz użyć **Page Up** i **Page Down** klucze przejście przez jeden ekran zasobów w danym momencie.

1. Wpisz nową wartość.

   Wartość natychmiast zmienia się w sekcjach ASCII i szesnastkowym i otrzymuje fokus do następnej wartości w wierszu.

> [!NOTE]
> **Edytor plików binarnych** automatycznie akceptuje zmian, po zamknięciu edytora.

### <a name="to-find-binary-data"></a>Aby znaleźć dane binarne

Można wyszukiwać ciągi ASCII lub bajty szesnastkowe. Na przykład, aby znaleźć *Hello*, możesz wyszukać albo ciągu *Hello* lub jego wartości szesnastkowej *48 65 6C 6 C 6 f*.

1. Przejdź do menu **Edytuj** > [znaleźć](/visualstudio/ide/reference/find-command).

1. W **Znajdź** Wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub typu danych, którą chcesz znaleźć.

1. Wybierz dowolny z **znaleźć** opcje, a następnie wybierz **Znajdź następny**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Aby utworzyć nowy zasób niestandardowy lub danych

Można utworzyć nowy zasób niestandardowy lub danych, umieszczając w oddzielnym pliku przy użyciu składni pliku skryptu (.rc) normalny zasób, a następnie w tym pliku zasobu, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierając polecenie  **Zasób zawiera**.

1. [Utwórz plik .rc](../windows/how-to-create-a-resource-script-file.md) zawierająca zasób niestandardowy lub danych.

   Niestandardowe dane można wpisać w pliku .rc, jako zakończony znakiem null cudzysłowie ciągi lub jako liczby całkowite w formacie dziesiętną, szesnastkowym lub ósemkowo.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik .rc projektu i wybierz **zasób zawiera**.

1. W **dyrektywy czasu kompilacji** wpisz `#include` instrukcję, która zawiera nazwę pliku zawierającego niestandardowego zasobu, na przykład:

    ```cpp
    #include mydata.rc
    ```

   Upewnij się, że składnia i pisownię możesz wpisać są poprawne. Zawartość **dyrektywy czasu kompilacji** pola są wstawiane do pliku skryptu zasobu, dokładnie tak, podczas ich wpisywania.

1. Wybierz **OK** zapisaniu zmian.

Innym sposobem na tworzenie zasobów niestandardowych jest zaimportować plik jako zasobów niestandardowych, zobacz [jak: Zarządzanie zasobami](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> Tworzenie nowych zasobów niestandardowych lub danych wymaga systemu Win32.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)