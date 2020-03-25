---
title: 'Instrukcje: zarządzanie zasobami (C++)'
ms.date: 02/14/2019
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
- vb.xmldesigner.data
- vs.resvw.resource.importing
- vc.resvw.resource.importing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
- .resx files [C++], editing
- resource files [C++], editing
- resx files [C++], editing
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 0af4e8faeb3d8606fb351b193364a2748fbc944e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215218"
---
# <a name="how-to-manage-resources-c"></a>Instrukcje: zarządzanie zasobami (C++)

## <a name="copy-and-edit-resources"></a>Kopiowanie i edytowanie zasobów

Można kopiować zasoby z jednego pliku do innego bez zmieniania ich lub zmiany języka lub warunku zasobu podczas jego kopiowania.

Można łatwo kopiować zasoby z istniejącego zasobu lub pliku wykonywalnego do bieżącego pliku zasobów. Aby skopiować zasoby, należy otworzyć oba pliki zawierające zasoby w tym samym czasie i przeciągnąć elementy z jednego pliku do innego lub skopiować i wkleić między dwoma plikami. Ta metoda działa w przypadku plików skryptów zasobów (. RC) i plików szablonów zasobów (. rct) oraz plików wykonywalnych (exe).

> [!NOTE]
> Wizualizacja C++ zawiera przykładowe pliki zasobów, których można użyć we własnej aplikacji. Aby uzyskać więcej informacji, zobacz [clipart: Common sources](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/general).

Nie można przeciągać i upuszczać, kopiować, wycinać ani wklejać plików zasobów w projekcie (**Widok zasobów**) i autonomicznych plikach. RC otwartych w oknach dokumentów. Można to zrobić w poprzednich wersjach produktu. Należy używać metody przeciągania i upuszczania między plikami. RC, które są otwarte poza projektem.

### <a name="to-copy-resources"></a>Aby skopiować zasoby

1. Otwórz oba pliki zasobów autonomicznie. (Zobacz [Używanie plików skryptów zasobów](how-to-create-a-resource-script-file.md#use-resource-script-files)). Na przykład Otwórz *Source1. RC* i *SOURCE2. RC*.

1. W pierwszym pliku. rc:

   - Korzystanie z metody przeciągania i upuszczania

      1. Wybierz zasób, który chcesz skopiować. Na przykład w *Source1. RC*wybierz pozycję **IDD_DIALOG1**.

      1. Przytrzymaj wciśnięty klawisz **Ctrl** i przeciągnij zasób do drugiego pliku. rc. Na przykład przeciągnij **IDD_DIALOG1** z *Source1. RC* do *SOURCE2. RC*.

         > [!TIP]
         > Przeciąganie zasobu bez przytrzymywania wciśniętego klawisza **Ctrl** przenosi zasób zamiast go kopiować.

   - Użycie metody copy i past

      1. Kliknij prawym przyciskiem myszy zasób, który chcesz skopiować (na przykład *Source1. RC*), a następnie wybierz polecenie **Kopiuj**.

      1. Kliknij prawym przyciskiem myszy plik zasobów, do którego chcesz wkleić zasób (na przykład *SOURCE2. RC*), a następnie wybierz polecenie **Wklej**.

> [!NOTE]
> Aby uniknąć konfliktów z nazwami symboli lub wartościami w istniejącym pliku, C++ Wizualizacja może zmienić wartość symbolu lub nazwę symbolu oraz wartość w czasie kopiowania do nowego pliku.

Podczas kopiowania w ramach zasobu można zmienić jego właściwość języka lub Właściwość Condition albo oba te elementy.

- Język zasobu określa język używany przez program [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) w celu ułatwienia zidentyfikowania zasobu, którego szukasz. Zasoby mogą mieć różnice dla każdego języka, które nie są związane z tekstem, na przykład akceleratory, które mogą działać tylko na klawiaturze japońskiej lub mapie bitowej, które byłyby odpowiednie tylko w przypadku kompilacji zlokalizowanych w języku chińskim.

- Warunek zasobu jest zdefiniowanym symbolem, który identyfikuje warunek, pod którym ta konkretna kopia zasobu ma być używana.

Język i warunek zasobu są wyświetlane w nawiasach po nazwie zasobu w oknie **obszaru roboczego** . W tym miejscu zasób o nazwie `IDD_AboutBox` używa `Finnish`, ponieważ jego język i jego warunek są `XX33`:

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Aby skopiować istniejący zasób i zmienić jego język lub warunek

W pliku *. RC* lub w oknie [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources) kliknij prawym przyciskiem myszy zasób, który chcesz skopiować, a następnie wybierz polecenie **Wstaw kopię**. Następnie ustaw następujące ustawienia:

- W polu Lista **Język** wybierz język.

- W polu **warunek** wpisz warunek.

### <a name="to-edit-resources"></a>Aby edytować zasoby

Pliki zasobów zarządzanych (. resx) to pliki XML. Po dodaniu zarządzanego pliku zasobów do projektu z okna dialogowego **Dodaj nowy element** domyślnie zostanie otwarty **Edytor zarządzanych zasobów** .

## <a name="import-and-export-resources"></a>Importowanie i eksportowanie zasobów

Możesz importować zasoby graficzne (mapy bitowe, ikony, kursory i paski narzędzi), pliki HTML i zasoby niestandardowe do użycia w wizualizacji C++. Można eksportować te same typy plików z projektu programu Visual Studio C++ do oddzielnych plików, które mogą być używane poza środowiskiem programistycznym.

> [!NOTE]
> Typów zasobów, takich jak akceleratory, okna dialogowe i tabele ciągów nie można importować ani eksportować, ponieważ nie są to typy plików autonomicznych.

### <a name="to-import-a-resource-into-the-resource-script-file"></a>Aby zaimportować zasób do pliku skryptu zasobu

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources) kliknij prawym przyciskiem myszy węzeł pliku skryptu zasobu (. RC), do którego chcesz dodać zasób, a następnie wybierz pozycję **Importuj**.

1. Znajdź i wybierz nazwę pliku mapy bitowej (. bmp), ikonę (. ico), kursor (. CUR), plik HTML (. htm) lub inny plik do zaimportowania.

1. Wybierz **przycisk OK** , aby dodać zasób do pliku skryptu zasobu.

> [!NOTE]
> Proces importowania działa tak samo niezależnie od wybranego typu zasobu. Zaimportowany zasób jest automatycznie dodawany do poprawnego węzła tego typu zasobu.

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>Aby wyeksportować zasób do użycia poza wizualizacjąC++

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)kliknij prawym przyciskiem myszy zasób, który chcesz wyeksportować, a następnie wybierz pozycję **Eksportuj**. Możesz zaakceptować bieżącą nazwę pliku lub wpisać nową.

1. Przejdź do folderu, w którym chcesz zapisać plik, a następnie wybierz pozycję **Eksportuj**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Instrukcje: Tworzenie zasobów](../windows/how-to-create-a-resource-script-file.md)<br/>
[Instrukcje: dołączanie zasobów w czasie kompilacji](../windows/how-to-include-resources-at-compile-time.md)
