---
title: 'Instrukcje: Tworzenie zasobów (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
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
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
- language-specific template files [C++]
- resource templates
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: 5a0bc6370d0973d63eb16ac992251531aa2e5193
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152394"
---
# <a name="how-to-create-resources-c"></a>Instrukcje: Tworzenie zasobów (C++)

> [!NOTE]
> **Edytor zasobów** lub **widok zasobów** nie jest dostępny w wersji Express.
>
> Te informacje nie ma zastosowania do zasobów w aplikacji klasycznych Windows lub aplikacji uniwersalnych platformy Windows. Projekty w językach .NET, nie używaj plików skryptu zasobu. Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [pliki zasobów](../windows/resource-files-visual-studio.md), [zasobów aplikacji i systemu zarządzania zasobów](/windows/uwp/app-resources/), i [zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

## <a name="create-a-resource-script"></a>Utwórz skrypt zasobów

Przed utworzeniem i dodawania nowych zasobów do projektu, należy najpierw utworzyć skrypt zasobu (plik .rc).

> [!NOTE]
> Skrypt zasobu (plik .rc) można dodać tylko do istniejącego projektu, który jest ładowany do środowiska IDE programu Visual Studio. Nie można utworzyć autonomiczny skrypt zasobu (spoza projektu). Szablony zasobów (.rct — pliki) mogą być tworzone w dowolnym momencie.

### <a name="to-create-a-resource-script"></a>Aby utworzyć skrypt zasobów

1. Umieść fokus na istniejący folder projektu w taki sposób, w **Eksploratora rozwiązań**, na przykład *MyProject*.

   > [!NOTE]
   > Nie należy mylić folderze projektu z folderu rozwiązania w **Eksploratora rozwiązań**. Jeśli fokus jest umieszczony na **rozwiązania** folderu, wyborów dokonanych w **Dodaj nowy element** okno dialogowe będzie różna.

1. Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

1. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Visual C++** kliknij folder **pliku zasobów (.rc)** w okienku po prawej stronie.

1. Podaj nazwę dla Twojego skryptu zasobu w **nazwa** tekst pola, a następnie wybierz **Otwórz**.

### <a name="to-open-a-resource-script"></a>Aby otworzyć skrypt zasobów

Zasoby można wyświetlić w skrypcie zasobów bez konieczności otwierania projektu. Plik skryptu zostanie otwarty w oknie dokumentu, w przeciwieństwie do otwarcia w **widok zasobów** okna (co jest wykonywane, gdy plik jest otwarty w projekcie).

> [!NOTE]
> Niektóre polecenia są dostępne tylko wtedy, gdy plik jest otwarty autonomiczny (spoza projektu). Otwieranie autonomicznego pliku oznacza, otwierając go bez pierwszego ładowania projektu.
>
> Na przykład, aby zapisać plik w innym formacie lub inną nazwę pliku (jako **Zapisz jako** polecenie jest niedostępne dla pliku w projekcie). Jeśli otworzysz pierwszy projekt za pomocą **pliku** > **Otwórz** > **projektu**, te polecenia są niedostępne.

Aby otworzyć skryptu zasobu spoza projektu:

1. Z **pliku** menu, wybierz opcję **Otwórz**, następnie wybierz **pliku**.

1. W **Otwórz plik** okno dialogowe, przejdź do pliku skryptu zasobów, zaznacz plik i wybierz pozycję **Otwórz**.

Aby otworzyć wiele skryptów zasobu spoza projektu:

1. Otwórz zarówno autonomiczne pliki zasobów. Na przykład otworzyć *Source1.rc* i *Source2.rc*.

1. Z **pliku** menu, wybierz **Otwórz**, a następnie wybierz **pliku**.

1. W **Otwórz plik** okno dialogowe, przejdź do pierwszego pliku skryptu zasobu, który chcesz otworzyć (*Source1.rc*), zaznacz plik i wybierz **Otwórz**.

1. Powtórz poprzedni krok, aby otworzyć drugiego pliku .rc (*Source2.rc*).

   Pliki .rc są teraz otwarte w oddzielnych dokumentów w systemie windows.

1. Gdy są otwarte, w obu plikach .rc **okna** wybierz menu lub kliknij prawym przyciskiem myszy jeden z plików .rc **nową grupę karta pozioma** lub **nowej grupie pionowej karcie**.

   Teraz są sąsiadująco systemu windows, dzięki czemu można je wyświetlić, jednocześnie.

Mogą wystąpić sytuacje, gdy chcesz wyświetlić zawartość pliku skryptu (.rc) zasobu projektu bez konieczności otwierania zasobu, np. okno dialogowe wewnątrz jego Edytor określonego zasobu. Na przykład można wyszukać ciąg we wszystkich oknach dialogowych w pliku zasobów bez konieczności otwierania każdej z nich osobno.

Łatwo można otworzyć pliku zasobów, w formacie tekstowym, aby wyświetlić wszystkie zasoby, które zawiera i ukończyć globalne operacje obsługiwane przez Edytor tekstu.

> [!NOTE]
> Edytory zasobów bezpośrednio odczytu nie .rc lub `resource.h` plików. Kompilator zasobów kompiluje je na .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne. Jak zwykłym skompilować procesu, informacje symboliczne (na przykład komentarzy) jest pomijany w procesie kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z pliku .rc, zostanie ponownie wygenerowany plik .rc (na przykład, gdy zapisujesz, Edytor zasobów zastępuje plik .rc i `resource.h` pliku). Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostaną utracone w przypadku, gdy plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu zachowanie komentarzy, wyświetlić [dołączanie zasobów w czasie kompilacji](../windows/how-to-include-resources-at-compile-time.md).

Aby otworzyć pliku skryptu zasobu w formacie tekstowym:

1. Z **pliku** menu wybierz opcję **Otwórz**, następnie wybierz **pliku**.

1. W **Otwórz plik** okno dialogowe, przejdź do pliku skryptu zasobów, którą chcesz wyświetlić w formacie tekstowym.

1. Zaznacz plik, a następnie wybierz strzałkę listy rozwijanej na **Otwórz** przycisk (po prawej stronie przycisku).

1. Wybierz **Otwórz za pomocą** z menu rozwijanego.

1. W **Otwórz za pomocą** okno dialogowe, wybierz opcję **Edytor kodu źródłowego (tekst)**.

1. Z **Otwórz jako** listy rozwijanej wybierz **tekstu**.

   Zasób, który zostanie otwarty w **kod źródłowy** edytora.

> [!TIP]
> Skrót jest kliknięcie prawym przyciskiem myszy plik .rc w **Eksploratora rozwiązań**, wybierz **Otwórz za pomocą...**  i wybierz **Edytor kodu źródłowego (tekst)**.

### <a name="to-add-mfc-support"></a>Aby dodać obsługę MFC

Normalnie Jeśli tworzenia aplikacji Microsoft Foundation Class (MFC) dla Windows przy użyciu [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), Kreator generuje zestaw podstawowych plików (w tym pliku zasobu skryptu (.rc)), które zawiera podstawowe funkcje MFC. Jednakże edytując plik .rc dla aplikacji Windows, nie jest oparty na bibliotece MFC, następujące funkcje MFC nie są dostępne:

Niektóre funkcje, które są specyficzne dla MFC obejmują kreatorzy kodu MFC, ciągi menu podpowiedzi, zawartość list dla formantów pola kombi i formantu ActiveX.

Aby dodać obsługę MFC do pliku skryptu zasobów:

1. Otwórz pliku skryptu zasobu.

1. W **widok zasobów**, wyróżnij folder zasobów (na przykład *MFC.rc*).

1. W [okno właściwości](/visualstudio/ide/reference/properties-window)ustaw **tryb MFC** właściwości **True**.

   > [!NOTE]
   > Oprócz ustawienia tej właściwości, plik .rc musi być częścią projektu MFC. Na przykład, ustawienie tylko **tryb MFC** do **True** na .rc pliku w projekcie systemu Win32 nie daje funkcji MFC.

## <a name="create-a-resource"></a>Tworzenie zasobu

Jako nowego zasobu domyślnego (zasób, który nie jest oparty na szablonie) lub jako zasób deseniem po szablonu, można utworzyć zasobu.

Podczas tworzenia nowego zasobu, Visual C++ przypisze unikatową nazwę, na przykład `IDD_Dialog1`. Tego Identyfikatora zasobu można dostosować, edytując właściwości zasobu w edytorze skojarzonego zasobu lub w [okno właściwości](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> Określać nazwy zasobu lub identyfikator, który jest zarezerwowany przez program Visual Studio. Zarezerwowane nazwy to DESIGNINFO, HWB i TEXTINCLUDE, a zarezerwowany identyfikator to 255.

**Widok zasobów** okno wyświetla plików zasobów znajdujących się w Twoich projektów. Rozwijanie folderu najwyższego poziomu (na przykład *Project1.rc*) zawiera typy zasobów w, że plik i rozwijanie każdego typu zasobu zawiera poszczególnych zasobów tego typu.

> [!TIP]
> Aby otworzyć okno Widok zasobów, wybierz **widok zasobów** na **widoku** menu (lub użyj **Ctrl** + **Shift**  +  **E**).
>
> Kliknij prawym przyciskiem myszy użyj **widok zasobów** okna do uruchamiania poleceń menu skrótów, lub kliknij dwukrotnie pasek tytułu, aby zadokować lub oddokować okno. Kliknij prawym przyciskiem myszy pasek tytułu zawiera dodatkowe polecenia, które pozwalają na kontrolę zachowania okna. Aby uzyskać więcej informacji, zobacz [zarządzania Windows](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Użyj **Dodaj zasób** okno dialogowe, aby dodać zasoby do projektu aplikacji pulpitu Windows C++ z następującymi właściwościami:

|Właściwość|Opis|
|-|-|
|**Typ zasobu**|Określa rodzaj zasobu, który chcesz utworzyć.<br/><br/>Można rozwinąć kursora i okna dialogowego pole zasobów kategorie, aby ujawnić dodatkowe zasoby. Te zasoby znajdują się w programie Visual Studio ...\Microsoft \<wersji\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Jeśli dodasz .rct — pliki, umieść je w tym katalogu lub określić inny [ścieżki dołączania](../windows/how-to-specify-include-directories-for-resources.md). Zasoby w tych plikach są następnie wyświetlane na drugim poziomie do odpowiedniej kategorii. Nie ma żadnych wstępnie limitu liczby .rct — pliki, które można dodać.<br/><br/>Zasoby pokazane na najwyższym poziomie w drzewie są domyślne zasoby, które są dostarczane przez program Visual Studio.|
|**Nowy**|Tworzy zasób, w zależności od typu wybranego w **typ zasobu** pole, a następnie otwiera zasobu w odpowiedniego edytora. Na przykład, jeśli tworzysz zasobu okna dialogowego, zostanie on otwarty w [Edytor okien dialogowych](../windows/dialog-editor.md).|
|**Importujuj**|Otwiera **zaimportować** okno dialogowe, w której można przejść do tego zasobu można mają zostać zaimportowane do bieżącego projektu. Możesz zaimportować mapy bitowej, ikony, kursor, HTML, dźwięku (. WAV) lub plik zasobów niestandardowych.|
|**Custom**|Otwiera **nowy niestandardowy zasób** okno dialogowe, w której utworzono zasób niestandardowy. Zasoby niestandardowe są jedynie edytować w edytorze binarnym.|

Użyj **nowy niestandardowy zasób** okno dialogowe, aby utworzyć nowy niestandardowy zasób w projekcie języka C++ z następującymi właściwościami:

|Właściwość|Opis|
|-|-|
|**Typ zasobu**|Umożliwia wprowadzenie nazwy niestandardowy typ zasobu w polu tekstowym. Visual C++ automatycznie powoduje rozpoczynanie nazwę podczas zamykania **nowy zasób niestandardowy** okno dialogowe.|

### <a name="to-create-a-new-resource"></a>Aby utworzyć nowy zasób

Można utworzyć nowy zasób, używając następujących czynności:

- W **widok zasobów**, wybierz swój plik .rc, a następnie wybierz **Edytuj** menu i wybrać **Dodaj zasób**. W **Dodaj zasób** okno dialogowe, wybierz typ zasobu, które chcesz dodać do projektu.

   > [!TIP]
   > Również kliknięciu prawym przyciskiem myszy plik .rc w **widok zasobów** i wybierz polecenie **Dodaj zasób** z menu skrótów.

- W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder projektu i wybierz **Dodaj**, następnie wybierz **Dodaj zasób** w menu skrótów. W **Dodaj zasób** okno dialogowe, wybierz typ zasobu, które chcesz dodać do projektu.

   > [!NOTE]
   > Jeśli nie masz jeszcze pliku .rc w projekcie, ten krok spowoduje utworzenie jednego. Następnie możesz powtórzyć ten krok, aby dodać określonych typów zasobów do nowego pliku .rc.

- W [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy klasy i wybierz polecenie **Dodaj**. Wybierz **Dodaj zasób** z menu skrótów i wybierz typ zasobu, które chcesz dodać do projektu.

- W **projektu** menu, wybierz **Dodaj zasób**.

## <a name="create-a-resource-template"></a>Utwórz szablon zasobu

Szablon zasobu jest dostosowane zasób, który został zapisany jako plik .rct. Szablonu usługi resource następnie służy jako punkt wyjścia do tworzenia zasobów. Szablony zasobów oszczędzić czas podczas opracowywania dodatkowe zasoby lub grupy zasobów, które udostępnianie funkcje, takie jak formanty standardowe lub powtarzające się elementy. Na przykład jeśli chcesz dołączyć przycisk Pomoc, za pomocą ikony logo firmy kilka okien dialogowych, Utwórz nowy szablon okno dialogowe i dostosować ją przy użyciu przycisku pomocy i logo.

Po dostosowaniu szablonu zasobów, należy zapisać te zmiany w folderze szablonu (lub w lokalizacji określonej w ścieżki dołączania) tak, że nowy szablon zasobu pojawią się w jego typ zasobu w **Dodaj zasób** okno dialogowe. Można teraz używać nowego szablonu zasobu tak często, zgodnie z potrzebami.

> [!NOTE]
> Edytor zasobów automatycznie zapewnia identyfikator unikatowy zasób Możesz poprawić [właściwości zasobu](../windows/changing-the-properties-of-a-resource.md) zgodnie z potrzebami.

> [!NOTE]
> Podkatalogi katalogu głównego szablonu, należy umieścić pliki szablonów specyficzne dla języka. Na przykład umieścić pliki szablonów angielskiej w... \\< katalog szablonu zasobów\>\1033. Visual Studio wyszukuje nowe pliki śledzenia RCT w programie Visual Studio \Program Files\Microsoft \<wersji\>\VC\VCResourceTemplates w programie Visual Studio \Program Files\Microsoft \<wersji > \VC\VCResourceTemplates\\< LCID\> (na przykład 1033 dla języka angielskiego), *lub* dowolnym miejscu [ścieżki dołączania](../windows/how-to-specify-include-directories-for-resources.md). Jeśli chcesz przechowywać pliki śledzenia RCT w innej lokalizacji, na przykład folder Moje dokumenty, musisz dodać ten folder do ścieżki dołączania, aby program Visual Studio można znaleźć pliku RCT.

### <a name="to-create-a-resource-template"></a>Aby utworzyć szablon zasobu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt.

1. Z menu skrótów wybierz **Dodaj**, następnie wybierz **Dodaj nowy element**.

1. W **Dodaj nowy element** dialogowym **szablonów:** okienku wybierz **plik szablonu zasobu (.rct)**.

1. Podaj nazwę i lokalizację nowego pliku .rct i wybierz pozycję **Otwórz**.

   Nowy plik .rct zostanie dodany do projektu i pojawia się w **Eksploratora rozwiązań** w obszarze **zasobów** folderu.

1. Kliknij dwukrotnie plik .rct, aby otworzyć go w oknie dokumentu. Aby dodać zasoby, kliknij prawym przyciskiem myszy plik w oknie dokumentu, a następnie wybierz **Dodaj zasób**.

   Można dostosować te zasoby i Zapisz plik .rct.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>Aby przekonwertować istniejącego pliku zasobów do szablonu

1. Otwórz plik .rc, jako autonomiczny plik.

1. Na **pliku** menu, wybierz opcję **Zapisz \< *filename*> jako**.

1. Określ lokalizację, a następnie wybierz **OK**.

### <a name="to-create-a-new-resource-from-a-template"></a>Aby utworzyć nowy zasób z szablonu

1. W **widok zasobów** okienku kliknij prawym przyciskiem myszy plik .rc i wybierz polecenie **Dodaj zasób** z menu skrótów.

1. W **Dodaj zasób** okna dialogowego wybierz znak plus (**+**) obok zasobu, aby rozwinąć węzeł zasobów i wyświetlić wszystkie szablony dostępne dla tego zasobu.

1. Dwukrotnie kliknij szablon, który chcesz użyć.

1. Zmodyfikuj dodano zasobów zgodnie z potrzebami w edytorze zasobów.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>
[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>