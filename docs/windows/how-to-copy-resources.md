---
title: 'Instrukcje: Zarządzanie zasobami (C++)'
ms.date: 11/04/2016
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
ms.openlocfilehash: e8b976f974e397b8012ebf59ede08ee64f4f7191
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150795"
---
# <a name="how-to-manage-resources-c"></a>Instrukcje: Zarządzanie zasobami (C++)

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-copy-resources"></a>Aby umożliwić kopiowanie zasobów

Możesz skopiować zasoby z jednego pliku do innego bez ich zmieniania lub zmienić języka lub warunku zasobu podczas kopiowania go.

Można go łatwo skopiować zasoby z istniejącego zasobu lub plik wykonywalny do bieżącego pliku zasobów. Aby umożliwić kopiowanie zasobów, możesz otworzyć oba pliki zawierające zasoby w tym samym czasie i przeciągnij elementy z jednego pliku lub skopiuj i Wklej między dwoma plikami. Ta metoda działa dla plików skryptu (.rc) zasobów i plików szablonów (.rct) zasobu, a także jako pliki wykonywalne (.exe).

> [!NOTE]
> Visual C++ zawiera przykładowe pliki zasobów, które można użyć w swojej aplikacji. Aby uzyskać więcej informacji, zobacz [CLIPART: Wspólnych zasobów](https://github.com/Microsoft/VCSamples).

Metodą przeciągania i upuszczania między plikami .rc, które są otwarte [poza projektem](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Aby umożliwić kopiowanie zasobów między plikami przy użyciu metody przeciągania i upuszczania

1. Otwórz zarówno autonomiczne pliki zasobów (Aby uzyskać więcej informacji, zobacz [wyświetlania zasobów w pliku .rc spoza projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Na przykład otworzyć *Source1.rc* i *Source2.rc*.

1. W pierwszym pliku .rc wybierz zasób, który chcesz skopiować. Na przykład w *Source1.rc*, wybierz opcję **IDD_DIALOG1**.

1. Naciśnij i przytrzymaj **Ctrl** klucza i przeciągnij go do drugiego pliku .rc. Na przykład przeciągać **IDD_DIALOG1** z *Source1.rc* do *Source2.rc*.

   > [!NOTE]
   > Przeciąganie zasób bez przytrzymywania **Ctrl** klucz przenosi zasobu, a nie skopiować go.

### <a name="to-copy-resources-using-copy-and-paste"></a>Do kopiowania zasobów za pomocą kopiowania i wklejania

1. Otwórz zarówno autonomiczne pliki zasobów (Aby uzyskać więcej informacji, zobacz [wyświetlania zasobów w pliku .rc spoza projektu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Na przykład *Source1.rc* i *Source2.rc*.

1. W pliku źródłowym, z którego chcesz skopiować zasobu (na przykład *Source1.rc*), kliknij prawym przyciskiem myszy zasób i wybierz polecenie **kopiowania** z menu skrótów.

1. Kliknij prawym przyciskiem myszy plik zasobów, do którego chcesz wkleić zasobu (na przykład *Source2.rc*). Wybierz **Wklej** z menu skrótów.

   > [!NOTE]
   > Użytkownik nie przeciągnij i upuść, kopiowanie, wycinanie lub wklejanie danych między plikami zasobów w projekcie (**widok zasobów**) i pliki .rc autonomicznej, (te otwarte w oknach dokumentów). Można to zrobić w poprzednich wersjach produktu.

   > [!NOTE]
   > Aby uniknąć konfliktów z nazwami symboli lub wartości z istniejącego pliku, Visual C++ może ulec zmianie wartości symboli zasobu przeniesionych lub nazwy symbolu i wartości po skopiuj go do nowego pliku.

### <a name="to-change-the-language-or-condition-of-a-resource-while-copying"></a>Aby zmiana języka lub warunku zasobu podczas kopiowania

Podczas kopiowania w zasobach, można zmienić jego właściwość języka i/lub właściwości warunku.

- Język zasobu identyfikuje taką, języka zasobu. Język jest używany przez [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) ułatwia zidentyfikowanie zasobów, dla których potrzebujesz. (Jednak zasoby mogą znajdować się różnic dla każdego z języków, które nie są związane z tekstu, na przykład tworzy akceleratorów, które może działać wyłącznie względem klawiatury japońskiej lub mapy bitowej, która byłaby tylko odpowiednie dla zlokalizowanego języka chińskiego)

- Stan zasobu jest zdefiniowany symbol, który określa warunek, w ramach której ma zostać użyty określonej kopii zasobu.

Język i warunku zasobu są wyświetlane w nawiasie po nazwie zasobu w **obszaru roboczego** okna. W tym przykładzie zasobu o nazwie `IDD_AboutBox` używa `Finnish` jako języka i jego stan jest `XX33`.

```cpp
IDD_AboutBox (Finnish - XX33)
```

Aby skopiować istniejący zasób i zmień jego języka lub warunku:

1. W pliku .rc, lub w [widok zasobów](../windows/resource-view-window.md) okna, kliknij prawym przyciskiem myszy zasób, którego chcesz skopiować.

1. Wybierz **Wstaw kopiowania** z menu skrótów.

1. W **Wstaw kopię zasobu** okno dialogowe:

   - Aby uzyskać **języka** pola listy, wybierz język.

   - W **warunek** wpisz warunek.

## <a name="to-edit-managed-resource-files"></a>Edytowanie zarządzanych plików zasobów

Zarządzanych plików zasobów (.resx) są plikami XML. Po dodaniu plik zasobu zarządzanego projektu z **Dodaj nowy element** okno dialogowe **Edytor zasobów zarządzanych** domyślnie otwierany.

## <a name="to-import-and-export-resources"></a>Importowanie i eksportowanie zasobów

Możesz zaimportować zasobów graficznych (map bitowych, ikon, kursorów i pasków narzędzi), pliki HTML i zasobów niestandardowych do użytku w programie Visual C++. Możesz wyeksportować te same typy plików z projektu języka Visual C++ w oddzielnych plikach, które mogą być używane poza środowiskiem programowania.

> [!NOTE]
> Typy zasobów, takich jak akceleratorów, okna dialogowe i tabele ciągów nie można zaimportować lub wyeksportować, ponieważ nie są one typy plików autonomicznych.

### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>Aby zaimportować pojedynczy zasób do Twojego bieżącego pliku zasobu

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy węzeł skrypt zasobu (* .rc) plik, do którego chcesz dodać do zasobu.

1. Wybierz **importu** w menu skrótów.

1. Znajdź i wybierz nazwę pliku, mapa bitowa (bmp), ikona (.ico), kursora (.cur), plik Html (.htm) lub innego pliku, który chcesz zaimportować.

1. Wybierz **OK** można dodać zasobu do wybranego pliku w **zasobów** widoku.

   > [!NOTE]
   > Wybrane działa proces importowania, typ ten sam sposób niezależnie od tego, które określonego zasobu. Zaimportowane zasobów jest automatycznie dodawany do węzła poprawne dla tego typu zasobu.

### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Aby wyeksportować mapy bitowej, ikona lub kursor postaci oddzielnych plików (do użytku poza programem Visual C++)

1. W **zasobów** wyświetlić, kliknij prawym przyciskiem myszy zasób, którą chcesz wyeksportować.

1. Wybierz **wyeksportować** w menu skrótów.

1. W **Eksportuj zasób** okna dialogowego pole, zaakceptuj nazwę bieżącego pliku lub wpisać nową.

1. Przejdź do folderu, w którym chcesz zapisać plik i wybierz polecenie **wyeksportować**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)