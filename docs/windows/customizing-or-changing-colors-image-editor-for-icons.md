---
title: Dostosowywanie lub zmiana kolorów (Edytor obrazów dla ikon)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.customcolorselector
helpviewer_keywords:
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
ms.assetid: e58f6b32-f435-4d9a-a570-7569433661ae
ms.openlocfilehash: 7ab353ad0aa22c74eeba58e9310d9bc0f8d5a832
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560286"
---
# <a name="customizing-or-changing-colors-image-editor-for-icons"></a>Dostosowywanie lub zmiana kolorów (Edytor obrazów dla ikon)

**Obraz** edytora [paleta kolorów](../windows/colors-window-image-editor-for-icons.md) początkowo wyświetlane są kolory standardowe 16. Z wyświetlonej kolorów można również utworzyć kolory niestandardowe. Następnie możesz [zapisać i załadować dostosowany palety kolorów](../windows/saving-and-loading-different-color-palettes-image-editor-for-icons.md).

**Selektor kolorów niestandardowych** okno dialogowe umożliwia dostosowanie kolorów, użyj dla obrazu. Następujące właściwości zawarte są:

|Właściwość|Opis|
|---|---|
|**Wyświetlanie kolor gradientu**|Umożliwia zmianę wartości wybrany kolor. Umieść krzyżyk kolor, który chcesz zmienić. Przesuń suwak w górę lub w dół, Zmień jasność lub wartości RGB koloru.|
|**Jasność paska**|Ustawia jasność koloru w **gradientu wyświetlania kolorów** pole. Wybierz i przeciągnij białe Strzałka w górę paska dla jasności większy lub w dół za niższą cenę. **Kolor** polu jest wyświetlana Kolor wybrano i efekt jasność ustawisz.|
|**Kolor**|Wyświetla listę aplikacji hue (wartość koło kolorów) kolor, który jest definiowany. Wartości z zakresu od 0 do 240, gdzie 0 jest czerwony, 60 jest żółty, 120 jest zielony, 180 jest błękitny, 200 jest amarantowy i 240 ma kolor niebieski.|
|**HUE**|Wyświetla listę aplikacji hue (wartość koło kolorów) kolor, który jest definiowany. Wartości z zakresu od 0 do 240, gdzie 0 jest czerwony, 60 jest żółty, 120 jest zielony, 180 jest błękitny, 200 jest amarantowy i 240 ma kolor niebieski.|
|**NAS.**|Określa wartość nasycenie koloru, który jest definiowany. Nasycenie jest ilość koloru w określonym odcieniu. Wartości z zakresu od 0 do 240.|
|**Jaskr.**|Wyświetla listę jasności (jasność) kolor, który jest definiowany. Wartości z zakresu od 0 do 240.|
|**Czerwony**|Określa wartość czerwony kolor, który jest definiowany. Wartości z zakresu od 0 do 255.|
|**Zielony**|Określa wartość zielony kolor, który jest definiowany. Wartości z zakresu od 0 do 255.|
|**Niebieski**|Określa wartość niebieskiego kolor, który jest definiowany. Wartości z zakresu od 0 do 255.|

## <a name="to-change-colors-on-the-colors-palette"></a>Aby zmienić kolory palety kolorów

1. Z **obraz** menu, wybierz **Dopasuj kolory**.

1. W **selektor kolorów niestandardowych** okna dialogowego pole, Zdefiniuj kolor, wpisując wartości RGB lub HSL w odpowiednie pola tekstowe lub wybierz kolor w **gradientu wyświetlania kolorów** pole.

1. Ustaw jasność za pomocą suwaka **jasność** paska.

1. Wiele kolorów niestandardowych są symulowane. Pełny kolor najbliżej kolor symulowany, kliknij dwukrotnie **kolor** pole.

   Jeśli później zdecydujesz, ma kolor symulowany, przesuń suwak **jasność** pasek lub przenieść krzyżyka **gradientu wyświetlania kolorów** okno ponownie, aby przywrócić symulowania kolorów.

1. Wybierz **OK** Aby dodać nowy kolor.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Menu obrazu](../windows/image-menu-image-editor-for-icons.md)<br/>
[Okno kolory](../windows/colors-window-image-editor-for-icons.md)