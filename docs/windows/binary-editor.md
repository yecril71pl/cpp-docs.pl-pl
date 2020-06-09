---
title: Edytor binarny (C++)
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
ms.openlocfilehash: 955cce012ac30c3413d7d458e263643d0aefa711
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615346"
---
# <a name="binary-editor-c"></a>Edytor binarny (C++)

> [!CAUTION]
> Edytowanie zasobów, takich jak okna dialogowe, obrazy lub menu w **edytorze binarnym** , jest niebezpieczne. Nieprawidłowa edycja może spowodować uszkodzenie zasobu, co sprawia, że nie można go odczytać w edytorze macierzystym.

**Edytor binarny** umożliwia edytowanie dowolnego zasobu na poziomie binarnym w formacie szesnastkowym lub ASCII. Możesz również użyć [polecenia Znajdź](/visualstudio/ide/reference/find-command) , aby wyszukać ciągi ASCII lub bajty szesnastkowe. Używaj **edytora binarnego** tylko wtedy, gdy musisz wyświetlać lub wprowadzać drobne zmiany zasobów niestandardowych lub typów zasobów nieobsługiwanych przez środowisko programu Visual Studio. **Edytor binarny** nie jest dostępny w wersjach Express.

- Aby otworzyć **Edytor binarny** w nowym pliku, przejdź do menu **plik**  >  **Nowy**  >  **plik**, wybierz typ pliku, który chcesz edytować, a następnie wybierz strzałkę rozwijaną obok przycisku **Otwórz** , a następnie wybierz **Otwórz za pomocą**  >  **edytora binarnego**.

- Aby otworzyć **Edytor binarny** w istniejącym pliku, przejdź do menu **plik**  >  ,**Otwórz**  >  **plik**, wybierz plik, który chcesz edytować, a następnie wybierz strzałkę listy rozwijanej obok przycisku **Otwórz** , a następnie wybierz **Otwórz za pomocą**  >  **edytora binarnego**.

   ![Edytor binarny](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   Dane binarne okna dialogowego wyświetlanego w **edytorze binarnym**

Tylko niektóre wartości ASCII są reprezentowane w **edytorze binarnym** (0X20 – 0x7E). Znaki rozszerzone są wyświetlane jako okresy w sekcji wartość ASCII w prawym panelu w **edytorze binarnym**. Drukowalne znaki to wartości ASCII od 32 do 126.

> [!TIP]
> Korzystając z **edytora binarnego**, w wielu wystąpieniach można kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów poleceń dotyczących zasobów. Dostępne polecenia zależą od elementów wskazywanych przez kursor. Na przykład po kliknięciu prawym przyciskiem myszy, gdy wskażesz **Edytor binarny** z wybranymi wartościami szesnastkowymi, menu skrótów pokaże polecenia **wycinania**, **kopiowania**i **wklejania** .

## <a name="how-to"></a>Instrukcje

**Edytor binarny** umożliwia:

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Aby otworzyć zasób pulpitu systemu Windows na potrzeby edycji plików binarnych

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)wybierz określony plik zasobów, który chcesz edytować.

1. Kliknij prawym przyciskiem myszy zasób i wybierz polecenie **Otwórz dane binarne**.

> [!NOTE]
> Jeśli używasz okna **Widok zasobów** , aby otworzyć zasób z formatem, który nie jest rozpoznawany przez program Visual Studio, taki jak RCDATA lub zasób niestandardowy, zasób zostanie automatycznie otwarty w **edytorze binarnym**.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>Aby otworzyć zasób zarządzany na potrzeby edycji plików binarnych

1. W **Eksplorator rozwiązań**wybierz określony plik zasobów, który chcesz edytować.

1. Kliknij prawym przyciskiem myszy zasób i wybierz polecenie **Otwórz za pomocą**.

1. W oknie dialogowym **Otwórz za pomocą** wybierz pozycję **Edytor binarny**.

> [!NOTE]
> Możesz użyć [edytora obrazów](image-editor-for-icons.md) i **edytora binarnego** do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

### <a name="to-edit-a-resource"></a>Aby edytować zasób

Jeśli chcesz użyć **edytora binarnego** dla zasobu, który jest już edytowany w innym oknie edytora, Zamknij najpierw inne okno edytora.

1. Wybierz bajt, który chcesz edytować.

   Klawisz **Tab** przenosi fokus między sekcjami szesnastkowymi i ASCII w **edytorze binarnym**. Możesz użyć klawiszy **Page Up** i **Page Down** , aby poruszać się po jednym ekranie zasobu w danym momencie.

1. Wpisz nową wartość.

   Wartość zmieni się natychmiast w sekcjach szesnastkowych i ASCII i fokus przesunie się na następną wartość w wierszu.

> [!NOTE]
> **Edytor binarny** akceptuje zmiany automatycznie po zamknięciu edytora.

### <a name="to-find-binary-data"></a>Aby znaleźć dane binarne

Można wyszukiwać ciągi ASCII lub bajty szesnastkowe. Na przykład, aby znaleźć *powitanie*, można wyszukać ciąg *Hello* lub jego wartość szesnastkową, *48 65 6c 6c 6F*.

1. Przejdź do menu **Edycja**  >  [Znajdź](/visualstudio/ide/reference/find-command).

1. W polu **Znajdź** , wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz dane, które chcesz znaleźć.

1. Wybierz dowolną z opcji **Znajdź** i wybierz pozycję **Znajdź dalej**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Aby utworzyć nowy zasób niestandardowy lub dane

Nowy zasób niestandardowy lub dane można utworzyć, umieszczając zasób w osobnym pliku przy użyciu standardowej składni pliku skryptu zasobów (. RC), a następnie uwzględniając ten plik, klikając prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierając pozycję **zasoby**.

1. [Utwórz plik. RC](how-to-create-a-resource-script-file.md) , który zawiera zasób niestandardowy lub dane.

   Możesz wpisać dane niestandardowe w pliku. RC jako ciągi cudzysłowów zakończonych znakiem null lub jako liczby całkowite w formacie dziesiętnym, szesnastkowym lub ósemkowym.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik. rc projektu i wybierz pozycję **zasób zawiera**.

1. W polu **dyrektywy czasu kompilacji** wpisz `#include` instrukcję, która zawiera nazwę pliku zawierającego zasób niestandardowy, na przykład:

    ```cpp
    #include mydata.rc
    ```

   Upewnij się, że składnia i pisownia wartości wpisanej są poprawne. Zawartość pola **dyrektywy kompilacji** jest wstawiana do pliku skryptu zasobu dokładnie podczas jego wpisywania.

1. Wybierz **przycisk OK** , aby zapisać zmiany.

Innym sposobem na utworzenie zasobu niestandardowego jest zaimportowanie pliku zewnętrznego jako zasobu niestandardowego, zobacz [How to: Manage Resources](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> Tworzenie nowych zasobów niestandardowych lub danych wymaga Win32.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](resource-editors.md)
