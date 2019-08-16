---
title: Projektant wstążki (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 1634eee30063a48041d60fc1b7116ca9543c9de2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511462"
---
# <a name="ribbon-designer-mfc"></a>Projektant wstążki (MFC)

Projektant wstążki umożliwia tworzenie i dostosowywanie wstążki w aplikacjach MFC. Wstążka to element interfejsu użytkownika, który organizuje polecenia w grupy logiczne. Te grupy są wyświetlane na oddzielnych kartach w obrębie górnej części okna. Wstążka zastępuje pasek menu i paski narzędzi. Wstążka może znacząco poprawić użyteczność aplikacji. Aby uzyskać więcej informacji, zobacz [wstążki](/windows/win32/uxguide/cmd-ribbons). Na poniższej ilustracji przedstawiono Wstążkę.

![Kontrolka zasobów wstążki MFC](../mfc/media/ribbon_no_callouts.png "Kontrolka zasobów wstążki MFC")

We wcześniejszych wersjach programu Visual Studio, wstążki musiały zostać utworzone przez napisanie kodu, który używa klas wstążki MFC, takich jak [Klasa CMFCRibbonBar](../mfc/reference/cmfcribbonbar-class.md). W programie Visual Studio 2010 i nowszych Projektant wstążki udostępnia alternatywną metodę tworzenia wstążki. Najpierw utwórz i Dostosuj Wstążkę jako zasób. Następnie załaduj zasób wstążki z kodu w aplikacji MFC. Można nawet jednocześnie używać zasobów wstążki i klas wstążki MFC. Na przykład można utworzyć zasób wstążki, a następnie programowo dodać do niego więcej elementów w czasie wykonywania przy użyciu kodu.

## <a name="understanding-the-ribbon-designer"></a>Omówienie projektanta wstążki

Projektant wstążki tworzy i przechowuje Wstążkę jako zasób. Podczas tworzenia zasobu wstążki Projektant wstążki wykonuje następujące trzy czynności:

- Dodaje wpis w skrypcie definicji zasobu projektu (*. RC). W poniższym przykładzie IDR_RIBBON jest unikatową nazwą, która identyfikuje zasób wstążki, RT_RIBBON_XML jest typem zasobu, a wstążka. mfcribbon-ms to nazwa pliku zasobów.

```
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- Dodaje definicje identyfikatorów poleceń do Resource. h.

```
#define IDR_RIBBON            307
```

- Tworzy plik zasobów wstążki (*. mfcribbon-ms) zawierający kod XML definiujący przyciski, kontrolki i atrybuty wstążki. Zmiany wstążki w Projektancie wstążki są przechowywane w pliku zasobów jako XML. Poniższy przykład kodu przedstawia część zawartości \*pliku. mfcribbon-ms:

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

Aby użyć zasobu wstążki w aplikacji MFC, Załaduj zasób przez wywołanie [CMFCRibbonBar:: LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Tworzenie wstążki przy użyciu projektanta wstążki

Są to dwa sposoby dodawania zasobu wstążki do projektu MFC:

- Utwórz aplikację MFC i skonfiguruj Kreatora projektu MFC, aby utworzyć Wstążkę. Aby uzyskać więcej informacji, [zobacz Przewodnik: Tworzenie aplikacji wstążki za pomocą MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

- W istniejącym projekcie MFC Utwórz zasób wstążki i załaduj go. Aby uzyskać więcej informacji, [zobacz Przewodnik: Aktualizowanie aplikacji bazgrołów MFC (część 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).

Jeśli projekt ma już ręcznie zakodowaną Wstążkę, MFC ma funkcje, których można użyć do przekonwertowania istniejącej wstążki na zasób wstążki. Aby uzyskać więcej informacji, zobacz [jak: Konwertuj istniejącą Wstążkę MFC na zasób](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md)wstążki.

> [!NOTE]
>  Wstążke nie mogą być tworzone w aplikacjach opartych na oknach dialogowych. Aby uzyskać więcej informacji, zobacz [Typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="customizing-ribbons"></a>Dostosowywanie wstążki

Aby otworzyć Wstążkę w Projektancie wstążki, kliknij dwukrotnie zasób wstążki w Widok zasobów. W projektancie można dodawać, usuwać i dostosowywać elementy na Wstążce, przycisku aplikacji lub pasku narzędzi Szybki dostęp. Zdarzenia można także połączyć, na przykład klikając przycisk zdarzenia i zdarzenia menu, do metody w aplikacji.

Na poniższej ilustracji przedstawiono różne składniki w Projektancie wstążki.

![Projektant wstążki MFC](../mfc/media/ribbon_designer.png "Projektant wstążki MFC")

- **Formantów** Zawiera kontrolki, które można przeciągnąć do powierzchni projektanta.

- **Powierzchnia projektanta:** Zawiera wizualną reprezentację zasobu wstążki.

- **Okno Właściwości:** Wyświetla listę atrybutów elementu, który jest zaznaczony na powierzchni projektanta.

- **Okno Widok zasobów:** Przedstawia zasoby, które obejmują zasoby wstążki w projekcie.

- **Pasek narzędzi edytora wstążki:** Zawiera polecenia, które umożliwiają podgląd wstążki i zmianę jej motywu wizualnego.

W poniższych tematach opisano, jak używać funkcji w Projektancie wstążki:

- [Instrukcje: dostosowywanie przycisku Aplikacja](../mfc/how-to-customize-the-application-button.md)

- [Instrukcje: dostosowywanie paska narzędzi Szybki dostęp](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [Instrukcje: dodawanie kontrolek wstążki do programów obsługi zdarzeń](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [Instrukcje: ładowanie zasobu wstążki z aplikacji MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>Definicje elementów wstążki

![Wstążka MFC](../mfc/media/ribbon.png "Wstążka MFC")

- **Przycisk aplikacji:** Przycisk, który pojawia się w lewym górnym rogu wstążki. Przycisk aplikacji zastępuje menu plik i jest widoczny nawet wtedy, gdy wstążka jest zminimalizowana. Po kliknięciu przycisku zostanie wyświetlone menu zawierające listę poleceń.

- **Pasek narzędzi Szybki dostęp:** Niewielki, dostosowywalny pasek narzędzi, który wyświetla często używane polecenia.

- **Kategoria**: Grupowanie logiczne, które reprezentuje zawartość karty wstążki.

- **Przycisk domyślny kategorii:** Przycisk, który pojawia się na Wstążce, gdy wstążka jest zminimalizowana. Gdy przycisk zostanie kliknięty, kategoria jest ponownie wyświetlana jako menu.

- **Płaski** Obszar paska wstążki, który wyświetla grupę powiązanych kontrolek. Każda kategoria wstążki zawiera co najmniej jeden panel wstążki.

- **Elementy wstążki:** Kontrolki w panelach, na przykład przyciski i pola kombi. Aby zobaczyć różne kontrolki, które mogą być hostowane na Wstążce, [Zobacz przykład RibbonGadgets: Aplikacja](../overview/visual-cpp-samples.md)gadżetów wstążki.

## <a name="see-also"></a>Zobacz także

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Praca z plikami zasobów](../windows/working-with-resource-files.md)
