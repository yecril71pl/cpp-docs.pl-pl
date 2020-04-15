---
title: Projektant wstążki (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 8b66ff0f19392eb1685f8632a3fc4d9e90094304
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372802"
---
# <a name="ribbon-designer-mfc"></a>Projektant wstążki (MFC)

Projektant wstążki umożliwia tworzenie i dostosowywanie wstążek w aplikacjach MFC. Wstążka jest elementem interfejsu użytkownika, który organizuje polecenia w grupy logiczne. Grupy te są wyświetlane na oddzielnych kartach w pasku w górnej części okna. Wstążka zastępuje pasek menu i paski narzędzi. Wstążka może znacznie poprawić użyteczność aplikacji. Aby uzyskać więcej informacji, zobacz [Wstążki](/windows/win32/uxguide/cmd-ribbons). Na poniższej ilustracji przedstawiono wstążkę.

![Kontrola zasobu wstążki MFC](../mfc/media/ribbon_no_callouts.png "Kontrola zasobu wstążki MFC")

We wcześniejszych wersjach programu Visual Studio wstążki musiały zostać utworzone przez pisanie kodu, który używa klas wstążki MFC, takich jak [CMFCRibbonBar Class](../mfc/reference/cmfcribbonbar-class.md). W programie Visual Studio 2010 i nowszych projektant wstążki udostępnia alternatywną metodę tworzenia wstążek. Najpierw utwórz i dostosuj wstążkę jako zasób. Następnie załaduj zasób wstążki z kodu w aplikacji MFC. Można nawet użyć zasobów wstążki i klas wstążki MFC razem. Na przykład można utworzyć zasób wstążki, a następnie programowo dodać więcej elementów do niego w czasie wykonywania przy użyciu kodu.

## <a name="understanding-the-ribbon-designer"></a>Opis Projektanta wstążki

Projektant wstążki tworzy i przechowuje wstążkę jako zasób. Podczas tworzenia zasobu wstążki projektant wstążki wykonuje następujące trzy czynności:

- Dodaje wpis w skrypcie definicji zasobu projektu (*.rc). W poniższym przykładzie IDR_RIBBON jest unikatową nazwą identyfikującą zasób wstążki, RT_RIBBON_XML jest typem zasobu, a ribbon.mfcribbon-ms jest nazwą pliku zasobu.

```cpp
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- Dodaje definicje identyfikatorów poleceń do pliku resource.h.

```
#define IDR_RIBBON            307
```

- Tworzy plik zasobu wstążki (*.mfcribbon-ms), który zawiera kod XML definiujący przyciski, formanty i atrybuty wstążki. Zmiany na wstążce w projektancie wstążki są przechowywane w pliku zasobu jako XML. Poniższy przykład kodu pokazuje część \*zawartości pliku .mfcribbon-ms:

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

Aby użyć zasobu wstążki w aplikacji MFC, załaduj zasób, wywołując [CMFCRibbonBar::LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Tworzenie wstążki przy użyciu Projektanta wstążki

Oto dwa sposoby dodawania zasobu wstążki do projektu MFC:

- Utwórz aplikację MFC i skonfiguruj Kreatora projektów MFC, aby utworzyć wstążkę. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie aplikacji wstążki przy użyciu MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

- W istniejącym projekcie MFC utwórz zasób wstążki i załaduj go. Aby uzyskać więcej informacji, zobacz [Przewodnik: Aktualizowanie aplikacji bazgrołów MFC (część 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).

Jeśli projekt ma już ręcznie zakodowane wstążki, MFC ma funkcje, których można użyć do konwersji istniejącej wstążki do zasobu wstążki. Aby uzyskać więcej informacji, zobacz [Jak: Konwertowanie istniejącej Wstążki MFC na zasób wstążki](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md).

> [!NOTE]
> W aplikacjach opartych na oknach dialogowych nie można tworzyć taśm. Aby uzyskać więcej informacji, zobacz [Typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="customizing-ribbons"></a>Dostosowywanie wstążek

Aby otworzyć wstążkę w projektancie wstążki, kliknij dwukrotnie zasób wstążki w widoku zasobu. W projektancie można dodawać, usuwać i dostosowywać elementy na wstążce, przycisku Aplikacji lub pasku narzędzi szybki dostęp. Można również połączyć zdarzenia, na przykład zdarzenia kliknięcia przycisku i zdarzenia menu, do metody w aplikacji.

Na poniższej ilustracji przedstawiono różne składniki w projektancie wstążki.

![Projektant wstążki MFC](../mfc/media/ribbon_designer.png "Projektant wstążki MFC")

- **Przybornik:** Zawiera formanty, które można przeciągać na powierzchnię projektanta.

- **Powierzchnia projektanta:** Zawiera wizualną reprezentację zasobu wstążki.

- ** [Kreator zajęć:](reference/mfc-class-wizard.md)** Wyświetla listę atrybutów elementu wybranego na powierzchni projektanta.

- **Okno Widok zasobu:** Wyświetla zasoby, które zawierają zasoby wstążki, w projekcie.

- **Pasek narzędzi Edytora wstążki:** Zawiera polecenia, które umożliwiają podgląd wstążki i zmianę jej motywu wizualnego.

W poniższych tematach opisano sposób używania funkcji w projektancie wstążki:

- [Porady: dostosowywanie przycisku Aplikacja](../mfc/how-to-customize-the-application-button.md)

- [Porady: dostosowywanie paska narzędzi Szybki dostęp](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [Instrukcje: dodawanie kontrolek wstążki do programów obsługi zdarzeń](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [Instrukcje: ładowanie zasobu wstążki z aplikacji MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>Definicje elementów wstążki

![Wstążka MFC](../mfc/media/ribbon.png "Wstążka MFC")

- **Przycisk aplikacji:** Przycisk wyświetlany w lewym górnym rogu wstążki. Przycisk Aplikacja zastępuje menu Plik i jest widoczny nawet wtedy, gdy wstążka jest zminimalizowana. Po kliknięciu przycisku zostanie wyświetlone menu z listą poleceń.

- **Pasek narzędzi Szybki dostęp:** Mały, konfigurowalny pasek narzędzi, na który wyświetlane są często używane polecenia.

- **Kategoria**: Logiczne grupowanie reprezentujące zawartość karty wstążki.

- **Domyślny przycisk Kategoria:** Przycisk wyświetlany na wstążce po zminimalizowaniu wstążki. Po kliknięciu przycisku kategoria pojawia się ponownie jako menu.

- **Panel:** Obszar paska wstążki, na którym jest wyświetlana grupa powiązanych formantów. Każda kategoria wstążki zawiera jeden lub więcej paneli wstążki.

- **Elementy wstążki:** Formanty w panelach, na przykład przyciski i pola kombi. Aby wyświetlić różne kontrolki, które mogą być hostowane na wstążce, zobacz [RibbonGadgets Sample: Ribbon Gadgets Application](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Praca z plikami zasobów](../windows/working-with-resource-files.md)
