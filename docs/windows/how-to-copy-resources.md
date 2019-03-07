---
title: 'Instrukcje: Zarządzanie zasobami (C++)'
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
ms.openlocfilehash: 28127ea89fdba1b70988ced1d6004c0f914c66e2
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/07/2019
ms.locfileid: "57563046"
---
# <a name="how-to-manage-resources-c"></a>Instrukcje: Zarządzanie zasobami (C++)

## <a name="copy-and-edit-resources"></a>Kopiuj i edytowanie zasobów

Możesz skopiować zasoby z jednego pliku do innego bez ich zmieniania lub zmiana języka lub warunku zasobu podczas kopiowania go.

Można go łatwo skopiować zasoby z istniejącego zasobu lub plik wykonywalny do bieżącego pliku zasobów. Aby umożliwić kopiowanie zasobów, możesz otworzyć oba pliki zawierające zasoby w tym samym czasie i przeciągnij elementy z jednego pliku lub skopiuj i Wklej między dwoma plikami. Ta metoda działa dla plików skryptu (.rc) zasobów i plików szablonów (.rct) zasobu, a także jako pliki wykonywalne (.exe).

> [!NOTE]
> Visual C++ zawiera przykładowe pliki zasobów, które można użyć w swojej aplikacji. Aby uzyskać więcej informacji, zobacz [CLIPART: Wspólnych zasobów](https://github.com/Microsoft/VCSamples).

Użytkownik nie przeciągnij i upuść, kopiowanie, wycinanie lub wklejanie danych między plikami zasobów w projekcie (**widok zasobów**) i otwieranie plików .rc autonomicznego w oknach dokumentów. Można to zrobić w poprzednich wersjach produktu. Tylko metodą przeciągania i upuszczania między plikami .rc, które są otwarte poza projektem.

### <a name="to-copy-resources"></a>Aby umożliwić kopiowanie zasobów

1. Otwórz zarówno autonomiczne pliki zasobów (zobacz instrukcje [można otworzyć pliku skryptu zasobu](/how-to-create-a-resource-script-file#use-resource-script-files)). Na przykład otworzyć *Source1.rc* i *Source2.rc*.

1. Wewnątrz pierwszy plik .rc, albo:

   - Użyj metody przeciągania i upuszczania

      1. Wybierz zasób, który chcesz skopiować. Na przykład w *Source1.rc*, wybierz opcję **IDD_DIALOG1**.

      1. Naciśnij i przytrzymaj **Ctrl** klucza i przeciągnij go do drugiego pliku .rc. Na przykład przeciągać **IDD_DIALOG1** z *Source1.rc* do *Source2.rc*.

         > [!TIP]
         > Przeciąganie zasób bez przytrzymywania **Ctrl** klucz przenosi zasobu, a nie skopiować go.

   - Użyj kopiowania i wklejania — metoda

      1. Kliknij prawym przyciskiem myszy zasób z do kopiowania (na przykład *Source1.rc*) i wybierz polecenie **kopiowania**.

      1. Kliknij prawym przyciskiem myszy plik zasobów, do którego chcesz wkleić zasobu (na przykład *Source2.rc*) i wybierz polecenie **Wklej**.

> [!NOTE]
> Aby uniknąć konfliktów z nazwami symboli lub wartości z istniejącego pliku, Visual C++ może ulec zmianie wartości symboli zasobu przeniesionych lub nazwy symbolu i wartości po skopiuj go do nowego pliku.

Podczas kopiowania w zasobach, można zmienić jego właściwość języka i/lub właściwości warunku.

- Język zasobu określa język używany przez [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) ułatwia zidentyfikowanie zasobów, dla których potrzebujesz. Zasoby mogą znajdować się różnic dla każdego z języków, które nie są związane z tekstu, na przykład tworzy akceleratorów, które może działać wyłącznie względem klawiatury japońskiej lub mapy bitowej, który tylko jest odpowiednia dla języka chińskiego zlokalizowane.

- Stan zasobu jest zdefiniowany symbol, który określa warunek, w ramach której ma zostać użyty określonej kopii zasobu.

Język i warunku zasobu są wyświetlane w nawiasie po nazwie zasobu w **obszaru roboczego** okna. W tym miejscu zasobu o nazwie `IDD_AboutBox` używa `Finnish` jako języka i jego stan jest `XX33`:

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Aby skopiować istniejący zasób i zmień jego języka lub warunku

W *.rc* pliku lub [widok zasobów](../windows/resource-view-window.md) okna, kliknij prawym przyciskiem myszy zasób, o których chcesz skopiować, a następnie wybierz **Wstaw kopiowania**. Następnie określ następujące ustawienia:

- Aby uzyskać **języka** pola listy, wybierz język.

- W **warunek** wpisz warunek.

### <a name="to-edit-resources"></a>Edytowanie zasobów

Zarządzanych zasobów (.resx) są plikami XML. Po dodaniu plik zasobu zarządzanego projektu z **Dodaj nowy element** okno dialogowe **Edytor zasobów zarządzanych** domyślnie otwierany.

## <a name="import-and-export-resources"></a>Importowanie i eksportowanie zasobów

Możesz zaimportować zasobów graficznych (map bitowych, ikon, kursorów i pasków narzędzi), pliki HTML i zasobów niestandardowych do użytku w programie Visual C++. Możesz wyeksportować te same typy plików z projektu języka Visual C++ w oddzielnych plikach, które mogą być używane poza środowiskiem programowania.

> [!NOTE]
> Typy zasobów, takich jak akceleratorów, okna dialogowe i tabele ciągów nie można zaimportować lub wyeksportować, ponieważ nie zostało to jeszcze typów plików autonomicznych.

### <a name="to-import-a-resource-into-the-resource-script-file"></a>Aby importować zasób do pliku skryptu zasobu

1. W [widok zasobów](../windows/resource-view-window.md) kliknij prawym przyciskiem myszy węzeł pliku skryptu (.rc) zasobu, do którego chcesz dodać zasób, a następnie wybierz pozycję **importu**.

1. Znajdź i wybierz nazwę pliku mapy bitowej (bmp), ikony (.ico), kursora (.cur), plik html (.htm) lub inny plik do zaimportowania.

1. Wybierz **OK** można dodać zasobu do pliku skryptu zasobów.

> [!NOTE]
> Proces importowania działa tak samo niezależnie od tego, typ zasobu, który wybrano. Zaimportowane zasobów jest automatycznie dodawany do poprawny węzeł tego typu zasobu.

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>Aby wyeksportować zasób do użycia poza programem Visual C++

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy zasób, chcesz wyeksportować, a następnie wybierz pozycję **wyeksportować**. Można zaakceptować bieżącej nazwy pliku lub wpisać nową.

1. Przejdź do folderu, w którym chcesz zapisać plik i wybierz **wyeksportować**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Instrukcje: Utwórz zasoby](../windows/how-to-create-a-resource-script-file.md)<br/>
[Instrukcje: dołączanie zasobów w czasie kompilacji](../windows/how-to-include-resources-at-compile-time.md)<br/>