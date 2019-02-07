---
title: Menu obrazu (C++ edytor obrazów dla ikon)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
helpviewer_keywords:
- Image menu
- Grid Settings dialog box [C++]
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
ms.openlocfilehash: e7d7d92401d5910cbb8aba8ab4c6000eca45cb01
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849733"
---
# <a name="image-menu-c-image-editor-for-icons"></a>Menu obrazu (C++ edytor obrazów dla ikon)

**Obraz** menu, która jest wyświetlana tylko wtedy, gdy **obraz** edytora jest aktywny, zawiera polecenia służące do edycji obrazów, zarządzanie palety kolorów i ustawienie **edytora obrazów** okna Opcje. Ponadto polecenia narzędzia obrazach urządzeń są dostępne podczas pracy z ikony i kursory.

|Polecenie|Opis|
|---|---|
|**Odwróć kolory**|Odwraca kolory. Aby uzyskać więcej informacji, zobacz [odwracanie kolorów w wyborze](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).|
|**Przerzuć w poziomie**|Przerzuca obraz lub zaznaczenie w poziomie. Aby uzyskać więcej informacji, zobacz [Przerzucanie obrazu](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Przerzuć w pionie**|Przerzuca obraz lub zaznaczenie w pionie. Aby uzyskać więcej informacji, zobacz [Przerzucanie obrazu](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Obrót o 90 stopni**|Obraca obraz lub zaznaczenie o 90 stopni. Aby uzyskać więcej informacji, zobacz [Przerzucanie obrazu](../windows/flipping-an-image-image-editor-for-icons.md).|
|**Pokaż okno kolorów**|Otwiera [okno kolorów](../windows/colors-window-image-editor-for-icons.md), w którym możesz wybrać kolory używane dla obrazu. Aby uzyskać więcej informacji, zobacz [Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md).|
|**Użyj zaznaczenia jako pędzla**|Umożliwia tworzenie pędzla niestandardowego na podstawie część obrazu. Wybór staje się pędzla niestandardowego, który rozdziela kolorów w wyborze między obrazu. Kopiuje zaznaczenie są pozostawiane w ścieżce przeciągania. Przeciągniesz wolniej, większej liczby kopii zostały wprowadzone. Aby uzyskać więcej informacji, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).|
|**Kopiuj i wybór konspektu**|Tworzy kopię bieżącego zaznaczenia i zakreśla ją. Jeśli kolor tła znajduje się w bieżącym zaznaczeniu, będzie on wykluczony, jeśli masz [przezroczyste](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) wybrane.
|**Adjust Colors**|Otwiera [selektor kolorów niestandardowych](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), co pozwala dostosować kolory używane dla obrazu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie lub zmiana kolorów](../windows/customizing-or-changing-colors-image-editor-for-icons.md).|
|**Załaduj paletę**|Otwiera [Załaduj paletę kolorów, okno dialogowe](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), co umożliwia ładowanie kolorów palety wcześniej zapisane w pliku .pal.|
|**Zapisz paletę**|Zapisuje w pliku .pal kolorów palety.|
|**Rysuj nieprzezroczyste**|Po wybraniu sprawia, że bieżące zaznaczenie nieprzezroczystości. Po wyczyszczeniu, sprawia, że bieżące zaznaczenie przezroczyste. Aby uzyskać więcej informacji, zobacz [wybierania nieprzezroczyste lub przezroczyste tło](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|**Edytor paska narzędzi**|Otwiera [okno dialogowe Nowy zasób paska narzędzi](../windows/new-toolbar-resource-dialog-box.md).|
|**Ustawienia siatki**|Otwiera **ustawienia siatki** okno dialogowe, w którym można określić siatki dla obrazu.|
|**Nowy typ obrazu**|Otwiera [New \<urządzenia > okno dialogowe typu obrazu](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Zasób pojedyncza ikona może zawierać kilka obrazów o różnych rozmiarach i system windows może używać rozmiar odpowiednią ikonę w zależności od tego, w jaki sposób będzie mają być wyświetlane. Nowy typ urządzenia nie modyfikuje rozmiar ikony, ale raczej tworzy nowy obraz w ramach ikony. Dotyczy tylko ikony i kursory.|
|**Bieżący typ obrazu ikony/kursora**|Spowoduje otwarcie podmenu zawierającego pierwszy dostępnych kursorem lub ikonę obrazów (dziewięć pierwszy). Ostatnie polecenie, w podmenu, **więcej...** , otwiera [Otwórz \<urządzenia > okno dialogowe obrazu](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Usuń typ obrazu**|Usuwa obraz wybranego urządzenia.|
|**Narzędzia**|Uruchamia podmenu, który zawiera wszystkie dostępne narzędzia [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md).|

**Ustawienia siatki** okno dialogowe umożliwia określenie ustawienia siatki dla obrazu i prezentuje linie siatki edytowanego obrazu. Wiersze są przydatne w przypadku edycji obrazu, ale nie są zapisywane jako część samego obrazu.

|Właściwość|Opis|
|---|---|
|**Siatka pikseli**|Po zaznaczeniu tej opcji, wyświetla siatkę wokół każdego piksela w edytorze obrazu. Siatka pojawia się tylko na 4 x i wyższych rozdzielczościach.|
|**Siatka**|Po wybraniu Wyświetla siatkę wokół bloki pikseli w edytorze obrazu, określony przez wartości odstępy siatki.|
|**Szerokość**|Określa szerokość każdy blok kafelka. Ta właściwość jest przydatna, gdy mapy bitowe zawierające wiele obrazów, które są rozmieszczone w regularnych odstępach czasu.|
|**Wysokość**|Określa wysokość każdego bloku kafelka. Ta właściwość jest przydatna, gdy mapy bitowe zawierające wiele obrazów, które są rozmieszczone w regularnych odstępach czasu.|

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz także

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Zmiana rozmiaru obrazu](../windows/resizing-an-image-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)