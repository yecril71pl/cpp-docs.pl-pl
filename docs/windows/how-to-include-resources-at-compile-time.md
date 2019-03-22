---
title: 'Instrukcje: Dołączanie zasobów w czasie kompilacji (C++)'
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
ms.openlocfilehash: cd2f05b4944e26d8a96b3f96e4e39fda0ad8ee48
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328392"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Instrukcje: Dołączanie zasobów w czasie kompilacji (C++)

Domyślnie wszystkie zasoby znajdują się w jednym pliku skryptu (.rc) zasobu jednak istnieje wiele przyczyn można umieścić zasoby w pliku innych niż plik .rc główne:

- Aby dodać komentarze do instrukcji zasobów, które nie będą usuwane podczas zapisywania pliku .rc.

- Aby dołączyć zasoby, które już opracowany i przetestowany i nie wymagają dalszych modyfikacji. Wszystkie pliki, które są uwzględniane, ale nie ma rozszerzenia .rc nie będzie można edytować za pomocą edytory zasobów.

- Aby dołączyć zasoby, które są używane przez różne projekty lub które są częścią systemu kontroli wersji kodu źródłowego. Te zasoby muszą istnieć w centralnej lokalizacji, w którym zmiany będzie miało wpływ na wszystkie projekty.

- Aby uwzględnić zasobów (takich jak zasoby RCDATA), które są formatu niestandardowego. Zasoby RCDATA mają specjalne wymagania, których nie można użyć wyrażenia jako wartość `nameID` pola.

Jeśli masz sekcje w istniejących plikach .rc, które spełniają dowolne z tych warunków, umieść następujące sekcje w jednym lub więcej oddzielnych plików .rc i umieszczone w projekcie za pomocą **zasób zawiera** okno dialogowe.

## <a name="resource-includes"></a>Zasób zawiera

Możesz dodać zasoby z innych plików do projektu w czasie kompilacji przez wymienienie ich w **dyrektywy czasu kompilacji** pole w **zasób zawiera** okno dialogowe. Użyj **zasób zawiera** okno dialogowe, aby zmodyfikować środowisko projektu normalnej pracy rozmieszczenie przechowywania wszystkich zasobów w pliku .rc projektu, a wszystkie [symbole](../windows/symbols-resource-identifiers.md) w `Resource.h`.

Aby rozpocząć, otwórz **zasób zawiera** okno dialogowe, klikając prawym przyciskiem myszy plik .rc w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), wybierz opcję **zasób zawiera** i zanotuj następujące właściwości:

| Właściwość | Opis |
|---|---|
| **Plik nagłówkowy symboli** | Umożliwia zmianę nazwy pliku nagłówkowego, w którym przechowywane są definicje symboli dla plików zasobów.<br/><br/>Aby uzyskać więcej informacji, zobacz [zmiana nazwy pliki nagłówkowe symboli](../windows/changing-the-names-of-symbol-header-files.md). |
| **Dyrektywy symboli tylko do odczytu** | Można dołączyć plików nagłówkowych, które zawierają symbole, które nie powinny być modyfikowane.<br/><br/>Na przykład pliki symboli być współużytkowane z innymi projektami. Może to również obejmować pliki .h MFC. Aby uzyskać więcej informacji, zobacz [tym udostępnionych (tylko do odczytu) lub symbole obliczane](../windows/including-shared-read-only-or-calculated-symbols.md). |
| **Dyrektywy czasu kompilacji** | Pozwala dołączyć pliki zasobów, które są tworzone i edytować oddzielnie z zasobów z głównego pliku zasobów, zawierać dyrektywy czasu kompilacji (takich jak te dyrektywy warunkowo obejmujące zasoby) lub zasobów w niestandardowym formacie.<br/><br/>Można również użyć **pole dyrektywy czasu kompilacji** obejmujący standardowe pliki zasobów biblioteki MFC. |

> [!NOTE]
> Wpisy w tych polach tekstowych pojawiają się w pliku .rc, oznaczony za `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, i `TEXTINCLUDE 3` odpowiednio. Aby uzyskać więcej informacji, zobacz [TN035: Przy użyciu wielu plików zasobów i plików nagłówków z programem Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Po dokonaniu zmian do pliku zasobów za pomocą **zasób zawiera** okno dialogowe, musisz zamknąć i ponownie otworzyć *.rc* pliku, aby zmiany zaczęły obowiązywać.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>Aby dołączyć zasoby do projektu w czasie kompilacji

1. Umieść zasoby w pliku skryptu zasobu przy użyciu unikatowej nazwy pliku. Nie używaj *projectname.rc*, ponieważ jest to nazwa pliku używany dla pliku skryptu zasobu głównego.

1. Kliknij prawym przyciskiem myszy *.rc* w pliku [widok zasobów](how-to-create-a-resource-script-file.md#create-resources) i wybierz **zasób zawiera**.

1. W **dyrektywy czasu kompilacji** Dodaj [#include](../preprocessor/hash-include-directive-c-cpp.md) dyrektywy kompilatora, które mają zostać objęte nowego pliku zasobu z głównego pliku zasobów w środowisku programistycznym.

Zasoby w plikach uwzględnione w ten sposób są wykonywane tylko część pliku wykonywalnego w czasie kompilacji i nie są dostępne do edycji lub modyfikacji, podczas pracy w pliku .rc głównego projektu. Pliki .rc dołączony muszą być otwarte osobno, a wszystkie pliki dołączone bez rozszerzenia .rc nie będzie można edytować za pomocą edytory zasobów.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>Do określenia katalogów dołączanych dla pliku określonego zasobu (.rc)

1. Kliknij prawym przyciskiem myszy *.rc* w pliku **Eksploratora rozwiązań** i wybierz **właściwości**.

1. Wybierz **zasobów** węzła w okienku po lewej stronie i określić wszelkie dodatkowe katalogi dołączane we **dodatkowe katalogi dołączane** właściwości.

### <a name="to-find-symbols-in-resources"></a>Aby znaleźć symboli w zasobach

1. Przejdź do menu **Edytuj** > [Znajdź Symbol](/visualstudio/ide/go-to).

   > [!TIP]
   > Aby użyć [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) wyszukiwania, wybierz [Znajdź w plikach](/visualstudio/ide/reference/find-command) w **Edytuj** menu zamiast **Znajdź Symbol**. Wybierz **użycia: Wyrażenia regularne** pole wyboru w [okno dialogowe Znajdź](/visualstudio/ide/finding-and-replacing-text) i **Znajdź** okno wyrażeń regularnych wyszukiwania można wybrać z listy rozwijanej. Po wybraniu wyrażenia z tej listy, zostanie zastąpiony jako wyszukiwany tekst w **Znajdź** pole.

1. W **Znajdź** Wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz klawisza skrótu, którą chcesz znaleźć, na przykład `ID_ACCEL1`.

1. Wybierz dowolny z **znaleźć** opcje, a następnie wybierz **Znajdź następny**.

> [!NOTE]
> Nie można wyszukiwać symbole w ciągu, akcelerator lub zasobów binarnych.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Instrukcje: Utwórz zasoby](../windows/how-to-create-a-resource-script-file.md)<br/>
[Instrukcje: Zarządzaj zasobami](../windows/how-to-copy-resources.md)<br/>