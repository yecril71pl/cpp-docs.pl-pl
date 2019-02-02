---
title: Zapisywanie i ładowanie różnych palet kolorów (Edytor obrazów dla ikon)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.color
- vc.editors.loadcolorpalette
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
ms.openlocfilehash: fd2664407d33d8e3ed594921501b7f80e6c8850b
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560273"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Zapisywanie i ładowanie różnych palet kolorów (Edytor obrazów dla ikon)

Można zapisać i załadować **kolory** palety, który zawiera [dostosować kolory](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (Domyślnie **kolory** palety ostatnio używane jest automatycznie ładowany podczas uruchamiania programu Visual Studio.)

> [!TIP]
> Ponieważ **obraz** edytor nie ma żadnych środków, aby przywrócić domyślne **kolory** palety, należy zapisać domyślne **kolory** palety w obszarze nazwy, takie jak  *Standard.PAL* lub *default.pal* tak, aby można je łatwo przywrócić ustawienia domyślne.

Użyj **ładowanie kolorów palety** okno dialogowe, aby załadować palety kolorów specjalne do użycia w projekcie języka C++. Następujące właściwości zawarte są:

|Właściwość|Opis|
|---|---|
|**Szukaj w**|Określa lokalizację, w którym chcesz zlokalizować pliku lub folderu. Wybierz strzałkę, aby wybrać inną lokalizację lub wybierz ikonę folderu, na pasku narzędzi, aby przenieść poziomów.|
|**Nazwa pliku**|Miejsce na wpisanie nazwy pliku, który chcesz otworzyć. Aby szybko znaleźć plik, który poprzednio otwarty, wybierz nazwę pliku na liście rozwijanej, jeśli jest dostępny.<br/><br/>Jeśli szukasz pliku można użyć gwiazdki (*) jako symboli wieloznacznych. Na przykład można wpisać \*.\* umożliwia wyświetlenie listy wszystkich plików. Możesz również wpisać pełną ścieżkę pliku, na przykład C:\My Documents\MyColorPalette.pal lub \\\NetworkServer\MyFolder\MyColorPalette.pal.|
|**Typy plików**|Zawiera listę typów plików do wyświetlenia. Paleta (* .pal) jest typem pliku domyślnej palety kolorów.|

## <a name="to-save-a-custom-colors-palette"></a>Aby zapisać palety kolorów niestandardowych

1. Z **obraz** menu, wybierz **Zapisz paletę**.

1. Przejdź do katalogu, w którym chcesz zapisać palety, a następnie wpisz nazwę palety.

1. Wybierz pozycję **Zapisz**.

## <a name="to-load-a-custom-colors-palette"></a>Aby załadować palety kolorów niestandardowych

1. Z **obraz** menu, wybierz **Załaduj paletę**.

1. W **Załaduj paletę kolorów** okna dialogowego pole, przejdź do katalogu poprawny i wybierz paletę chcesz załadować. **Kolor** palet są zapisywane wraz z rozszerzeniem pliku .pal.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)