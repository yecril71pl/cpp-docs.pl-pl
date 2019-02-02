---
title: Pasek narzędzi (C++ edytor obrazów dla ikon)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
helpviewer_keywords:
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
ms.assetid: a0af4209-6273-4106-a7c1-0edecc9b5755
ms.openlocfilehash: dfbd721afd997f3151b1c20a7e0e1fb60e0c83e4
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560325"
---
# <a name="toolbar-c-image-editor-for-icons"></a>Pasek narzędzi (C++ edytor obrazów dla ikon)

**Edytora obrazów** narzędzi zawiera narzędzia do rysowania, rysowania, wprowadzania tekstu, wymazywanie i manipulowanie widoków. Zawiera ona także Selektor opcji, za pomocą którego można wybrać opcje dotyczące korzystania z poszczególnych narzędzi. Na przykład można wybierać różne szerokość pędzla, czynniki powiększenia i style linii.

> [!NOTE]
> Wszystkie narzędzia dostępne na **edytora obrazów** narzędzi są także dostępne z **obraz** menu (w obszarze **narzędzia** polecenie).

![Pasek narzędzi edytora obrazów](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar") paska narzędzi edytora obrazów

Aby użyć **edytora obrazów** narzędzi i **opcji** selektor, wybierz narzędzie lub opcji, które mają.

> [!TIP]
> Etykietki narzędzi są wyświetlane po umieszczeniu kursora na przycisku paska narzędzi. Poniższe wskazówki mogą pomóc w identyfikacji funkcji każdego przycisku.

Za pomocą **opcji** selektor można określić szerokość linii, pociągnięć i nie tylko. Ikony na **opcji** selektor przycisk zmiany, w zależności od narzędzie, które zostały wybrane.

![Rysowanie&#45;selektor kształt na pasku narzędzi edytora obrazów](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector") Selektor opcji na pasku narzędzi edytora obrazów

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="use-the-text-tool-dialog-box"></a>Użyj okna dialogowego narzędzie tekstowe

Użyj **narzędzie tekstowe** okno dialogowe, aby dodać tekst do kursora, mapa bitowa lub ikona zasobu.

Aby uzyskać dostęp do tego okna dialogowego, otwórz [edytora obrazów](../windows/window-panes-image-editor-for-icons.md). Wybierz **narzędzia** z **obraz** menu, a następnie wybierz pozycję **narzędzie tekstowe** polecenia.

### <a name="font-button"></a>Przycisk Czcionka

Otwiera **narzędzie czcionki tekstu** okno dialogowe, w którym można zmienić czcionki, styl i rozmiar czcionki kursora. Zmiany są stosowane do tekstu wyświetlanego w **tekstu** obszaru.

Aby otworzyć to okno dialogowe, wybierz **czcionki** znajdujący się w **narzędzie tekstowe** okno dialogowe. Są dostępne właściwości:

|Właściwość|Opis|
|---|---|
|**Czcionka**|Wyświetla listę dostępnych czcionek.|
|**Styl czcionki**|Wyświetla listę dostępnych stylów określonej czcionki.|
|**Rozmiar**|Wyświetla listę dostępnych rozmiarów określonej czcionki.|
|**Próbki**|Pokazuje przykładowy wygląd tekstu przy użyciu ustawień określonej czcionki.|
|**Skrypt**|Wyświetla listę dostępnych skryptów językowych dla określonej czcionki. Po wybraniu inny język skryptu, zestawu znaków języka i udostępnieniu do tworzenia dokumentów w wielu języków.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>Zmiana czcionki tekstu obrazu

Poniższa procedura to przykład sposobu dodawania tekstu do ikony w aplikacji Windows i manipulowania czcionkę tekstu.

1. Tworzenie aplikacji formularzy Windows w języku C++. Aby uzyskać więcej informacji, zobacz [Tworzenie projektu aplikacji Windows](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5). *App.ico* plik zostanie dodany do projektu, domyślnie.

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie plik *app.ico*. [Edytora obrazów](../windows/image-editor-for-icons.md) zostanie otwarty.

1. Z **obraz** menu, wybierz opcję **narzędzia** , a następnie wybierz **narzędzie tekstowe**. **Narzędzie tekstowe** zostanie wyświetlone okno dialogowe.

1. W **narzędzie tekstowe** okno dialogowe, typ *C++* w obszarze pusty tekst. Ten tekst będzie wyświetlany w polu o zmiennym rozmiarze, znajduje się w lewym górnym rogu *app.ico*w **edytora obrazów**.

1. W **edytora obrazów**, przeciągnij pole o zmiennych rozmiarach do środka app.ico można zwiększyć czytelność tekstu.

1. W **narzędzie tekstowe** okno dialogowe, wybierz opcję **czcionki** przycisku. **Narzędzie czcionki tekstu** zostanie wyświetlone okno dialogowe.

1. W **narzędzie czcionki tekstu** okno dialogowe, wybierz opcję **podzbiory** z listy dostępnych czcionek, które są wymienione w **czcionki** pola listy.

1. Wybierz **Bold** z listy dostępnych style na liście **styl czcionki** pola listy.

1. Wybierz **10** z listy dostępnych punktów rozmiarów wymienionych w **rozmiar** pola listy.

1. Wybierz przycisk **OK**. **Narzędzie czcionki tekstu** okno dialogowe zostanie zamknięte i nowe ustawienia czcionek będą stosowane do tekstu.

1. Wybierz **Zamknij** znajdujący się na **narzędzie tekstowe** okno dialogowe. Pole o zmiennym rozmiarze wokół tekstu zniknie z **edytora obrazów**.

### <a name="text-area"></a>Obszar tekstu

Wyświetla tekst, który pojawia się jako część zasobu. Ten obszar jest początkowo pusta.

> [!NOTE]
> Jeśli **przezroczyste tło** jest ustawiona tylko tekst, zostaną umieszczone w obrazie. Jeśli **tło nieprzezroczyste** ustawiono prostokąt otaczający wypełnione [kolor tła](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md), zostaną umieszczone za tekstem. Aby uzyskać więcej informacji, zobacz [wybierając nieprzezroczystych i tło przezroczyste](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Kliknięciu prawym przyciskiem myszy **narzędzie tekstowe** okno dialogowe, aby dostęp do menu skrótów domyślne, które zawiera listę standardowych poleceń Windows.

## <a name="to-display-or-hide-the-image-editor-toolbar"></a>Aby wyświetlić lub ukryć pasek narzędzi edytora obrazów

Ponieważ wiele narzędzi do rysowania są dostępne z [klawiatury](../windows/accelerator-keys-image-editor-for-icons.md), warto czasami Ukryj **edytora obrazów** paska narzędzi.

Na **widoku** menu, wybierz opcję **pasków narzędzi** wybierz **edytora obrazów**.

   > [!NOTE]
   > Elementy z tego paska narzędzi pojawi się niedostępne, gdy plik obrazu z bieżącego projektu lub rozwiązania nie jest otwarty w **edytora obrazów**. Zobacz [Tworzenie ikony lub innego obraz](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), aby uzyskać informacje dotyczące dodawania plików obrazów do swoich projektów.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Okno kolory](../windows/colors-window-image-editor-for-icons.md)<br/>
[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>