---
title: Tworzenie, przenoszenie i edytowanie przycisków paska narzędzi (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: d0f0c6c6-9d7e-42b5-a86a-7558127386e7
ms.openlocfilehash: 2a67123e444ad208eaae74a24b72288f2dbb3bdb
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742703"
---
# <a name="creating-moving-and-editing-toolbar-buttons-c"></a>Tworzenie, przenoszenie i edytowanie przycisków paska narzędzi (C++)

Można łatwo utworzyć, przenoszenie, kopiowanie i edytowanie przycisków paska narzędzi.

Domyślnie przycisk Nowy lub pusty jest wyświetlany po prawej stronie paska narzędzi. Możesz przenieść ten przycisk, przed jego edycji. Podczas tworzenia nowego przycisku po prawej stronie przycisku edycji pojawi się kolejny przycisk puste. Pasek narzędzi, pusty przycisk nie jest zapisywany.

Właściwości przycisku paska narzędzi są:

|Właściwość|Opis|
|--------------|-----------------|
|**Identyfikator**|Określa identyfikator przycisku. Listy rozwijanej udostępnia typowe **identyfikator** nazwy.|
|**Szerokość**|Określa szerokość przycisku. zalecane jest 16 pikseli.|
|**Wysokość**|Określa wysokość przycisku. Wysokość jednego przycisku zmienia wysokość wszystkie przyciski na pasku narzędzi. Zaleca się 15 pikseli.|
|**wiersz**|Określa komunikat wyświetlany na pasku stanu. Dodawanie \n i nazwę dodaje etykietkę narzędzia do tego przycisku paska narzędzi. Aby uzyskać więcej informacji, zobacz [tworzeniem etykietki narzędzi](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Szerokość** i **wysokość** dotyczą wszystkich przycisków. Mapa bitowa, który jest używany do tworzenia paska narzędzi ma maksymalną szerokość 2048. Dlatego jeśli szerokość przycisku równa 512, może mieć tylko cztery przyciski i jeśli szerokość równa 513, może mieć tylko trzy przyciski.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

Zobacz następujące akcje:

## <a name="to-create-a-new-toolbar-button"></a>Aby utworzyć nowego przycisku paska narzędzi

1. W [widok zasobów](../windows/resource-view-window.md) rozwiń folder zasobów (na przykład *Project1.rc*).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Rozwiń **narzędzi** folder i wybierz pasek narzędzi do edycji.

1. Identyfikator należy przypisać pusty przycisk po prawej stronie paska narzędzi. Możesz to zrobić, edytując **identyfikator** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window). Na przykład można podać tej samej opcji menu przycisku paska narzędzi. W tym przypadku użyj pola listy rozwijanej, aby wybrać **identyfikator** opcji menu.

   —lub—

   Wybierz pusty przycisk po prawej stronie paska narzędzi (w **pasek narzędzi widoku** okienko) i rozpocząć rysowania. Domyślny przycisk polecenia identyfikator jest przypisywany (ID_BUTTON\<n >).

Można również skopiuj i Wklej obraz jest jako nowego przycisku paska narzędzi.

## <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Aby dodać obraz do paska narzędzi, jak przycisk

1. W [widok zasobów](../windows/resource-view-window.md), Otwórz pasek narzędzi, klikając go dwukrotnie.

1. Następnie otwórz obraz, który chcesz dodać do paska narzędzi.

   > [!NOTE]
   > Jeśli otworzysz go w programie Visual Studio, zostanie on otwarty w **obraz** edytora. Można również otworzyć obrazu w innych programach grafiki.

1. Z **Edytuj** menu, wybierz **kopiowania**.

1. Przejdź do paska narzędzi, wybierając jego kartę w górnej części okna źródła.

1. Z **Edytuj** menu, wybierz **Wklej**.

   Obraz pojawi się na pasku narzędzi jako nowy przycisk.

## <a name="to-move-a-toolbar-button"></a>Aby przenieść przycisk paska narzędzi

W **pasek narzędzi widoku** okienku przeciągnij przycisk, który ma zostać przeniesiony do nowej lokalizacji, na pasku narzędzi.

## <a name="to-copy-buttons-from-a-toolbar"></a>Kopiowanie przycisków z paska narzędzi

1. Naciśnij i przytrzymaj **Ctrl** klucza.

1. W **pasek narzędzi widoku** okienku przeciągnij przycisk do jednej nowej lokalizacji na pasku narzędzi lub do lokalizacji na inny pasek narzędzi.

## <a name="to-delete-a-toolbar-button"></a>Aby usunąć przycisku paska narzędzi

Wybierz przycisk paska narzędzi i przeciągnij go poza pasek narzędzi.

## <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>Aby wstawić lub usuwanie odstępów między przyciskami na pasku narzędzi

Ogólnie rzecz biorąc Aby wstawić odstęp między przyciskami, przeciągnij je od siebie nawzajem na pasku narzędzi. Aby usunąć przestrzeń, przeciągnij je do siebie nawzajem.

### <a name="to-insert-a-space-before-a-button-that-isnt-followed-by-a-space"></a>Aby wstawić odstęp przed przycisk, który nie jest następuje spacja

Przeciągnij przycisk po prawej stronie lub w dół do momentu widoczny w połowie o jej nakłada przycisk Dalej.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-to-keep-the-trailing-space"></a>Wstaw spację przed przycisk, który następuje spacja i zachować spacje końcowe

Przeciągnij przycisk, aż do prawej lub dolnej krawędzi zachodzi po prostu przycisk Dalej, lub po prostu nakłada się.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-close-up-that-following-space"></a>Wstaw spację przed przycisk, który następuje spacja i zamknąć tego następujące miejsce

Przeciągnij przycisk po prawej stronie lub w dół do momentu widoczny w połowie o jej nakłada przycisk Dalej.

### <a name="to-remove-a-space-between-buttons-on-a-toolbar"></a>Aby usunąć odstępów między przyciskami na pasku narzędzi

Przeciągnij przycisk na jednej stronie miejsca kierunku przycisku po drugiej stronie miejsca, dopóki nie nakłada się przycisk Następny temat w połowie.

   Jeśli nie ma już miejsca obok przycisku, który przeciąga opuszczenie i przycisk przeciągnąć ponad połowie ostatnie sąsiadujących przycisku **narzędzi** edytora również jest wstawiana w przeciwną stronę przycisku, który masz przeciąganie.

## <a name="to-change-the-properties-of-a-toolbar-button"></a>Aby zmienić właściwości przycisku paska narzędzi

1. W projekcie w języku C++ kliknij przycisk paska narzędzi.

1. Wpisz nowy identyfikator w **identyfikator** właściwość [okno właściwości](/visualstudio/ide/reference/properties-window), lub użyj listy rozwijanej, aby wybrać nowy **identyfikator**.

## <a name="requirements"></a>Wymagania

ATL i MFC

## <a name="see-also"></a>Zobacz też

[Edytor paska narzędzi](../windows/toolbar-editor.md)
