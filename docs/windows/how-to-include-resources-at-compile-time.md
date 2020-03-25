---
title: 'Instrukcje: uwzględnianie zasobów w czasie kompilacji (C++)'
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: e931a0246340e81049df6ed0f8e26a4b91b570c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215198"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Instrukcje: uwzględnianie zasobów w czasie kompilacji (C++)

Domyślnie wszystkie zasoby znajdują się w jednym pliku skryptu zasobu (. RC), ale istnieje wiele powodów, aby umieścić zasoby w pliku innym niż główny plik. rc:

- Aby dodać komentarze do instrukcji zasobów, które nie zostaną usunięte podczas zapisywania pliku. rc.

- Aby uwzględnić zasoby, które zostały już opracowane i przetestowane, i nie potrzebujesz dalszej modyfikacji. Wszystkie pliki, które są dołączone, ale nie mają rozszerzenia. RC, nie będą edytowalne przez edytory zasobów.

- Aby uwzględnić zasoby, które są używane przez różne projekty lub które są częścią systemu kontroli wersji kodu źródłowego. Te zasoby muszą znajdować się w centralnej lokalizacji, w której modyfikacje wpłyną na wszystkie projekty.

- Aby uwzględnić zasoby (takie jak zasoby RCDATA), które są niestandardowym formatem. Zasoby RCDATA mają specjalne wymagania, w przypadku których nie można użyć wyrażenia jako wartości pola `nameID`.

Jeśli masz sekcje w istniejących plikach. RC, które spełniają którykolwiek z tych warunków, Umieść te sekcje w jednym lub kilku oddzielnych plikach. RC, a następnie dołącz je do projektu przy użyciu okna dialogowego **zasób zawiera** .

## <a name="resource-includes"></a>Zasób obejmuje

Możesz dodać zasoby z innych plików do projektu w czasie kompilacji, umieszczając je w polu **dyrektywy kompilacji** w oknie dialogowym **zasób zawiera** . Za pomocą okna dialogowego **zasób zawiera** można modyfikować normalne działania środowiska projektu dotyczące przechowywania wszystkich zasobów w pliku Project. RC i wszystkich [symboli](../windows/symbols-resource-identifiers.md) w `Resource.h`.

Aby rozpocząć, Otwórz okno dialogowe **zasób zawiera** , klikając prawym przyciskiem myszy plik. rc w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources), wybierz pozycję **zasób zawiera** i zanotuj następujące właściwości:

| Właściwość | Opis |
|---|---|
| **Plik nagłówka symboli** | Pozwala zmienić nazwę pliku nagłówka, w którym są przechowywane definicje symboli dla plików zasobów.<br/><br/>Aby uzyskać więcej informacji, zobacz [zmiana nazw plików nagłówkowych symboli](../windows/changing-the-names-of-symbol-header-files.md). |
| **Dyrektywy symboli tylko do odczytu** | Umożliwia dołączenie plików nagłówkowych, które zawierają symbole, które nie powinny być modyfikowane.<br/><br/>Na przykład pliki symboli mają być współużytkowane z innymi projektami. Może to również obejmować pliki MFC. h. Aby uzyskać więcej informacji, zobacz [Włączanie symboli udostępnionych (tylko do odczytu) lub obliczonych](../windows/including-shared-read-only-or-calculated-symbols.md). |
| **Dyrektywy czasu kompilacji** | Umożliwia dołączenie plików zasobów, które są tworzone i edytowane niezależnie od zasobów w głównym pliku zasobów, zawierają dyrektywy czasu kompilowania (takie jak dyrektywy, które warunkowo obejmują zasoby) lub zawierają zasoby w formacie niestandardowym.<br/><br/>Możesz również użyć **pola dyrektywy czasu kompilacji** , aby uwzględnić standardowe pliki zasobów MFC. |

> [!NOTE]
> Wpisy w tych polach tekstowych pojawiają się w pliku. RC oznaczone odpowiednio `TEXTINCLUDE 1`, `TEXTINCLUDE 2`i `TEXTINCLUDE 3`. Aby uzyskać więcej informacji, zobacz [TN035: używanie wielu plików zasobów i plików nagłówkowych C++z wizualizacją ](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Po wprowadzeniu zmian w pliku zasobów przy użyciu okna dialogowego **zasób zawiera** należy zamknąć i ponownie otworzyć plik *. RC* , aby zmiany zaczęły obowiązywać.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>Aby uwzględnić zasoby w projekcie w czasie kompilacji

1. Umieść zasoby w pliku skryptu zasobu z unikatową nazwą pliku. Nie używaj *ProjectName. RC*, ponieważ jest to nazwa pliku używanego dla głównego pliku skryptu zasobu.

1. Kliknij prawym przyciskiem myszy plik *. RC* w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources) i wybierz pozycję **zasób zawiera**.

1. W polu **dyrektywy czasu kompilacji** Dodaj dyrektywę kompilatora [#include](../preprocessor/hash-include-directive-c-cpp.md) , aby uwzględnić nowy plik zasobów w głównym pliku zasobów w środowisku deweloperskim.

Zasoby w plikach zawarte w ten sposób są częścią pliku wykonywalnego w czasie kompilacji i nie są dostępne do edycji ani modyfikacji podczas pracy z głównym plikiem projektu. rc. Pliki. RC muszą być otwierane oddzielnie, a wszystkie pliki z rozszerzeniem. RC nie będą edytowalne przez edytorów zasobów.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>Aby określić katalogi dołączane dla określonego pliku zasobu (. RC)

1. Kliknij prawym przyciskiem myszy plik *. RC* w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**.

1. W lewym okienku wybierz węzeł **zasoby** i określ dodatkowe katalogi dołączane we właściwości **Dodatkowe katalogi dołączane** .

### <a name="to-find-symbols-in-resources"></a>Aby znaleźć symbole w zasobach

1. Przejdź do menu **Edycja** , > [znaleźć symbol](/visualstudio/ide/go-to).

   > [!TIP]
   > Aby używać [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) w wyszukiwaniu, wybierz pozycję [Znajdź w plikach](/visualstudio/ide/reference/find-command) w menu **Edycja** zamiast **symbolu Znajdź**. Zaznacz pole wyboru **Użyj: wyrażenia regularne** w oknie [dialogowym Znajdź](/visualstudio/ide/finding-and-replacing-text) , a następnie w polu **Znajdź** możesz wybrać wyrażenie regularne wyszukiwanie z listy rozwijanej. Po wybraniu wyrażenia z tej listy zostanie on zastąpiony jako tekst wyszukiwania w polu **Znajdź** .

1. W polu **Znajdź** , wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz klawisz akceleratora, który chcesz znaleźć, na przykład `ID_ACCEL1`.

1. Wybierz dowolną z opcji **Znajdź** i wybierz pozycję **Znajdź dalej**.

> [!NOTE]
> Nie można wyszukiwać symboli w zasobach typu String, Accelerator lub Binary.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Instrukcje: Tworzenie zasobów](../windows/how-to-create-a-resource-script-file.md)<br/>
[Instrukcje: zarządzanie zasobami](../windows/how-to-copy-resources.md)<br/>
