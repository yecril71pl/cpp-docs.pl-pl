---
title: 'Instrukcje: Tworzenie pliku skryptu zasobów (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
- rc files [C++], adding MFC support
- .rc files [C++], adding MFC support
- MFC, adding support to resource scripts files
- resource script files [C++], adding MFC support
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: 9055e0f787c238276d3134c2fa6a8afae0102433
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905683"
---
# <a name="how-to-create-a-resource-script-file-c"></a>Instrukcje: Tworzenie pliku skryptu zasobów (C++)

> [!NOTE]
> **Edytor zasobów** nie jest dostępny w wersji Express.
>
> W tym materiale dotyczy aplikacje pulpitu Windows. Projekty w językach .NET, nie używaj plików skryptu zasobu. Aby uzyskać więcej informacji, zobacz [pliki zasobów](../windows/resource-files-visual-studio.md).

## <a name="to-create-a-new-resource-script-rc-file"></a>Aby utworzyć nowego pliku zasobu skryptu (.rc)

1. Umieść fokus na istniejący folder projektu w taki sposób, w **Eksploratora rozwiązań**, na przykład `MyProject`.

   > [!NOTE]
   > Nie należy mylić folderze projektu z folderu rozwiązania w **Eksploratora rozwiązań**. Jeśli fokus jest umieszczony na **rozwiązania** folderu, wyborów dokonanych w **Dodaj nowy element** okno dialogowe (w kroku 3) będą inne.

1. Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Visual C++** kliknij folder **pliku zasobów (.rc)** w okienku po prawej stronie.

1. Podaj nazwę pliku skryptu zasobu w **nazwa** tekst pola, a następnie wybierz **Otwórz**.

Możesz teraz [tworzenie](../windows/how-to-create-a-resource.md) i dodawania nowych zasobów do pliku .rc.

> [!NOTE]
> Skrypt zasobu (plik .rc) można dodać tylko do istniejącego projektu, który jest ładowany do środowiska IDE programu Visual Studio. Nie można utworzyć autonomiczny plik .rc (po jednym spoza projektu). [Szablony zasobów](../windows/how-to-use-resource-templates.md) (.rct — pliki) można tworzyć w dowolnym momencie.

## <a name="to-open-a-resource-script-file-outside-of-a-c-project-standalone"></a>Można otworzyć pliku skryptu zasobu spoza projektu (autonomicznego) języka C++

Zasoby można wyświetlić w pliku .rc, bez konieczności jest otwarty projekt. Plik .rc zostanie otwarty w oknie dokumentu, w przeciwieństwie do otwarcia w [widok zasobów](../windows/resource-view-window.md) okna (co jest wykonywane, gdy plik jest otwarty w projekcie).

> [!NOTE]
> Jest to ważna różnica, ponieważ niektóre polecenia są dostępne tylko wtedy, gdy plik jest otwarty autonomiczny (spoza projektu). Na przykład, można tylko zapisywania pliku w innym formacie lub innej nazwy pliku po otwarciu pliku spoza projektu ( **Zapisz jako** polecenie jest niedostępne, gdy plik jest otwarty w projekcie).

### <a name="to-open-an-rc-file-outside-a-project"></a>Aby otworzyć plik .rc poza projektem

1. Z **pliku** menu, wybierz **Otwórz**, a następnie wybierz **pliku**.

1. W **Otwórz plik** okno dialogowe, przejdź do pliku skryptu zasobu, aby wyświetlić, zaznacz plik i wybierz **Otwórz**.

   > [!NOTE]
   > Jeśli Otwórz projekt (**pliku**, **Otwórz**, **projektu**), niektóre polecenia nie będą dostępne dla Ciebie. Otwieranie pliku "autonomicznej" oznacza, otwierając go bez pierwszego ładowania projektu.

### <a name="to-open-multiple-rc-files-outside-a-project"></a>Aby otworzyć wiele plików .rc poza projektem

1. Otwórz zarówno autonomiczne pliki zasobów. Na przykład otworzyć `Source1.rc` i `Source2.rc`.

   1. Z **pliku** menu, wybierz **Otwórz**, a następnie wybierz **pliku**.

   1. W **Otwórz plik** okno dialogowe, przejdź do pierwszego pliku skryptu zasobu, który chcesz otworzyć (`Source1.rc`), zaznacz plik i wybierz **Otwórz**.

   1. Powtórz poprzedni krok, aby otworzyć drugiego pliku .rc (`Source2.rc`).

       Pliki .rc są teraz otwarte w oddzielnych dokumentów w systemie windows.

1. Gdy oba pliki .rc są otwarte, Kafelek systemu windows, dzięki czemu można je wyświetlić, jednocześnie:

   - Z **okna** menu, wybierz **nową grupę karta pozioma** lub **nowej grupie pionowej karcie**.

       \- lub —

   - Kliknij prawym przyciskiem myszy jeden z plików .rc i wybierz polecenie **nową grupę karta pozioma** lub **nowej grupie pionowej karcie** z menu skrótów.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

## <a name="to-open-a-resource-script-file-in-text-format"></a>Można otworzyć pliku skryptu zasobu w formacie tekstowym

Mogą wystąpić sytuacje, gdy chcesz wyświetlić zawartość pliku skryptu (.rc) zasobu projektu bez konieczności otwierania zasobu, np. okno dialogowe wewnątrz jego Edytor określonego zasobu. Na przykład można wyszukać ciąg we wszystkich oknach dialogowych w pliku zasobów bez konieczności otwierania każdej z nich osobno.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

Łatwo można otworzyć pliku zasobów, w formacie tekstowym, aby wyświetlić wszystkie zasoby, które zawiera i ukończyć globalne operacje obsługiwane przez Edytor tekstu.

> [!NOTE]
> Edytory zasobów bezpośrednio odczytu nie .rc lub `resource.h` plików. Kompilator zasobów kompiluje je na .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne. Jak zwykłym skompilować procesu, informacje symboliczne (na przykład komentarzy) jest pomijany w procesie kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z pliku .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastąpi plików .rc i pliku resource.h). Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu zachowanie komentarzy, wyświetlić [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).

### <a name="to-open-a-resource-script-file-as-text"></a>Można otworzyć pliku skryptu zasobu jako tekst

1. Z **pliku** menu wybierz opcję **Otwórz**, następnie wybierz **pliku**.

1. W **Otwórz plik** okno dialogowe, przejdź do pliku skryptu zasobów, którą chcesz wyświetlić w formacie tekstowym.

1. Zaznacz plik, a następnie wybierz strzałkę listy rozwijanej na **Otwórz** przycisku (znajdujący się po prawej stronie przycisku).

1. Wybierz **Otwórz za pomocą** z menu rozwijanego.

1. W **Otwórz za pomocą** okno dialogowe, wybierz opcję **Edytor kodu źródłowego (tekst)**.

1. Z **Otwórz jako** listy rozwijanej wybierz **tekstu**.

   Zasób, który zostanie otwarty w **kod źródłowy** edytora.

\- lub —

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik .rc.

1. Z menu skrótów wybierz polecenie **Otwórz za pomocą...** , a następnie wybierz **Edytor kodu źródłowego (tekst)**.

## <a name="to-add-mfc-support-to-resource-script-files"></a>Aby dodać obsługę MFC do plików skryptu zasobu

Zwykle podczas kompilowania aplikacji MFC dla Windows przy użyciu [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), Kreator generuje zestaw podstawowych plików (w tym pliku zasobu skryptu (.rc)), który zawiera podstawowe funkcje programu Microsoft Foundation klasy (MFC). Jednak jeśli edytujesz plik .rc dla aplikacji Windows, który nie jest oparty na bibliotece MFC, następujące funkcje specyficzne dla platformy MFC nie są dostępne:

- Kreatorzy kodu MFC

- Ciągi menu podpowiedzi

- Zawartość list dla formantów pola kombi

- Obsługa formantu ActiveX

Można jednak dodać obsługę MFC do istniejących plików .rc, które go nie masz.

> [!NOTE]
> Te kroki wymagają MFC.

### <a name="to-add-mfc-support-to-rc-files"></a>Aby dodać obsługę MFC do plików .rc

1. Otwórz pliku skryptu zasobu.

1. W [widok zasobów](../windows/resource-view-window.md), wyróżnij folder zasobów (na przykład MFC.rc).

1. W [okno właściwości](/visualstudio/ide/reference/properties-window)ustaw **tryb MFC** właściwości **True**.

   > [!NOTE]
   > Oprócz ustawienia tej flagi, plik .rc musi być częścią projektu MFC. Na przykład, ustawienie tylko **tryb MFC** do **True** w pliku .rc w systemie Win32 projektu nie daje żadnych funkcji MFC.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)