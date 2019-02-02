---
title: Tworzenie obrazu urządzenia (Edytor obrazów dla ikon)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
ms.openlocfilehash: ce1069f6f410d7a60d631461086ca8870ef679c0
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560299"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>Tworzenie obrazu urządzenia (Edytor obrazów dla ikon)

Podczas tworzenia nowej ikony lub zasobu kursora **obraz** edytora najpierw tworzy obraz w określonym stylu (32 x 32, 16 kolorów dla ikony oraz 32 × 32, monochromatyczny liczby kursorów). Można dodać obrazy w różnych rozmiarach i style do początkowego ikony lub kursor i edytowania każdego dodatkowego obrazu zgodnie z potrzebami dla różnych ekranów. Można również edytować obraz przy użyciu operacji kopiowania i wklejania z istniejącego typu obrazu lub mapy bitowej utworzonej w programie graficznym.

Po otwarciu ikony zasobu w [edytora obrazów](../windows/image-editor-for-icons.md), obraz, większość ściśle dopasowując bieżące urządzenie wyświetlające jest domyślnie otwierany.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="new-ltdevicegt-image-type-dialog-box"></a>Nowe &lt;urządzenia&gt; okno dialogowe typu obrazu

**New &lt;urządzenia&gt; typ obrazu** okno dialogowe umożliwia utworzenie nowego obrazu urządzenia o określonym typie. Aby otworzyć **New \<urządzenia > obraz** okno dialogowe, wybierz opcję **nowy typ obrazu** na **obraz** menu. Następujące właściwości zawarte są **typ obrazu docelowego** i **niestandardowe**.

### <a name="target-image-type"></a>Docelowy typ obrazu

Wyświetla listę typów dostępnych obrazów. Wybierz typ obrazu, który chcesz otworzyć:

||||
|-|-|-|
|-16 x 16, 16 kolorów|-48 x 48, 16 kolorów|-96 x 96, 16 kolorów|
|-16 x 16, 256 kolorów|-48 x 48, 256 kolorów|-96 x 96, 256 kolorów|
|-16 x 16, monochromatyczny|-48 x 48, monochromatyczny|-96 x 96, monochromatyczny|
|-32 x 32, 16 kolorów|-64 x 64, 16 kolorów||
|-32 x 32, 256 kolorów|-64 x 64, 256 kolorów||
|-32 x 32, monochromatyczny|-64 x 64, monochromatyczny||

> [!NOTE]
> Żadnych istniejących obrazów, nie pojawi się na tej liście.

### <a name="custom"></a>Niestandardowe

Otwiera **obrazu niestandardowego** okno dialogowe, w którym można utworzyć nowy obraz niestandardowy rozmiar i liczba kolorów.

**Obrazu niestandardowego** okno dialogowe umożliwia utworzenie nowego obrazu z niestandardowy rozmiar i liczba kolorów. Następujące właściwości zawarte są:

|Właściwość|Opis|
|---|---|
|**Szerokość**|Miejsce na wprowadź szerokość obrazu niestandardowego w pikselach (1-512 limit 2048).|
|**Wysokość**|Miejsce na Wprowadź wysokość obrazu niestandardowego w pikselach (1-512 limit 2048).|
|**Kolory**|Miejsce na wybierz liczbę kolorów dla niestandardowego obrazu: 2, 16 lub 256.|

## <a name="open-ltdevicegt-image-dialog-box"></a>Otwórz &lt;urządzenia&gt; okno dialogowe obrazu

Użyj **Otwórz &lt;urządzenia&gt; obraz** okno dialogowe, aby otworzyć obrazach urządzeń w projektach C++. Wyświetla listę istniejących obrazów urządzeń w bieżącym (obrazy, które są częścią bieżącego zasobu). Następująca właściwość włączone jest:

|Właściwość|Opis|
|---|---|
|**Bieżących obrazów**|Wyświetla listę obrazów zawartych w zasobie. Wybierz typ obrazu, który chcesz otworzyć.|

## <a name="to-create-a-new-icon-or-cursor"></a>Aby utworzyć nową ikonę lub kursora

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Wstaw zasobów** z menu skrótów. (Jeśli masz już istniejący zasób obrazu w pliku .rc, takich jak kursora, możesz kliknąć prawym przyciskiem myszy **kursora** i wybierz polecenie **wstawiania kursora** z menu skrótów.)

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W [Wstaw zasób — okno dialogowe](../windows/add-resource-dialog-box.md), wybierz opcję **ikonę** lub **kursora** i wybierz polecenie **New**. Ikony ta akcja powoduje utworzenie przy użyciu 32 x 32, ikona 16 kolorów zasobu ikony. Dla kursorów, 32 x 32, tworzony jest monochromatyczny obrazu (w kolorze 2).

   Jeśli znak plus (**+**) pojawia się obok typ zasobu obrazu w **Wstaw zasobów** okno dialogowe, oznacza to, narzędzi szablony są dostępne. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie wybierz **New**.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Ikony i kursory: Zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Ikony i kursory: Zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[Menu obrazu](../windows/image-menu-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)<br/>
