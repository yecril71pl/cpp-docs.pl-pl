---
title: 'Instrukcje: Tworzenie zasobów (C++)'
ms.date: 02/14/2019
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
ms.openlocfilehash: 768675a878891ebb75c7f42c12eae8dfcfa3510b
ms.sourcegitcommit: e540706f4e2675e7f597cfc5b4f8dde648b007bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676490"
---
# <a name="how-to-create-resources-c"></a>Instrukcje: Tworzenie zasobów (C++)

Można utworzyć zasobów dla Twojego projektu przez:

- Przy użyciu pliku skryptu zasobu. Ten krok jest niezbędny, aby dodać zasoby.

- Dodawanie zasobów do projektu. W tym kroku przedstawiono sposób użycia **widok zasobów**.

- Tworzenie niestandardowych zasobów przy użyciu szablonu usługi resource

> [!NOTE]
> **Edytor zasobów** i **widok zasobów** nie są dostępne w wersji Express.

## <a name="use-resource-script-files"></a>Użyj plików skryptu zasobu

Przed utworzeniem i dodawania nowych zasobów do projektu, należy najpierw utworzyć pliku zasobu skryptu (.rc).

> [!NOTE]
> Skrypt zasobu można dodać tylko do istniejącego projektu załadowana do środowiska IDE programu Visual Studio. Nie można utworzyć skrypt zasobu autonomicznych, poza projektem, chociaż szablony zasobów (.rct — pliki) mogą być tworzone w dowolnym momencie.

### <a name="to-create-a-resource-script-file"></a>Aby utworzyć plik skryptu zasobu

1. Umieść fokus na istniejący folder projektu w taki sposób, w **Eksploratora rozwiązań**, na przykład *MyProject*.

   > [!NOTE]
   > Nie należy mylić folderze projektu z folderu rozwiązania w **Eksploratora rozwiązań**. Jeśli fokus jest umieszczony na **rozwiązania** folderu, nie będzie mieć taką samą **Dodaj nowy element** wyborów.

1. W menu, przejdź do **projektu** > **Dodaj nowy element**.

1. Wybierz **Visual C++** folder i wybierz polecenie **pliku zasobów (.rc)** w okienku po prawej stronie.

1. Podaj nazwę pliku skryptu zasobu w **nazwa** pola tekstowego, a następnie wybierz **Otwórz**.

### <a name="to-open-a-resource-script-file"></a>Można otworzyć pliku skryptu zasobu

Bez konieczności otwierania projektu, można wyświetlić zasobów w pliku skryptu zasobu. Otwiera plik skryptu w oknie dokumentu, w przeciwieństwie do **widok zasobów**.

> [!NOTE]
> Niektóre polecenia są dostępne tylko jeśli plik jest otwarty autonomicznej, co oznacza spoza projektu lub bez niej pierwszy podczas ładowania projektu. Na przykład, aby użyć **Zapisz jako** polecenia, aby zapisać plik pod inną nazwą pliku lub formatu, plik musi być otwarty autonomicznych.

- Aby otworzyć pliku skryptu zasobu spoza projektu, w menu, przejdź do **pliku** > **Otwórz**i wybierz polecenie **pliku**. Następnie przejdź do pliku skryptu zasobu, zaznacz plik i wybierz polecenie **Otwórz**.

  - Można otworzyć pliku skryptu zasobu w formacie tekstowym, użyj strzałki listy rozwijanej w prawej części **Otwórz** znajdujący się w kroku powyżej i wybierz **Otwórz za pomocą**. Następnie wybierz pozycję **Edytor kodu źródłowego (tekst)** i **Otwórz jako** listy rozwijanej wybierz **tekstu**, i zasobów zostanie otwarty w **kod źródłowy**edytora.

    > [!NOTE]
    > Mogą wystąpić sytuacje, gdy chcesz wyświetlić zawartość pliku skryptu zasobu projektu bez użycia edytory zasobów, aby otworzyć zasobu. Na przykład można wyszukać ciąg we wszystkich oknach dialogowych w pliku zasobów bez konieczności otwierania każdej z nich osobno. Łatwo można otworzyć pliku zasobów, w formacie tekstowym, aby wyświetlić wszystkie zasoby, które zawiera i ukończyć globalne operacje obsługiwane przez Edytor tekstu.

- Do otwarcia wielu zasobu skrypty wykonaj powyższe kroki dla każdego pliku, który chcesz otworzyć, na przykład *Source1.rc* i *Source2.rc*. Następnie, gdy oba pliki .rc są otwarte w oddzielnym dokumenty w systemie windows, albo użyć **okna** menu lub kliknij prawym przyciskiem myszy jeden z plików .rc i wybierz pozycję **nową grupę karta pozioma** lub **nowe tabulator pionowy Grupa**. Teraz są sąsiadująco systemu windows, dzięki czemu można je wyświetlić, jednocześnie.

> [!TIP]
> Pliki skryptów zasobów można również otworzyć, klikając prawym przyciskiem myszy plik .rc w **Eksploratora rozwiązań**, wybierając **Otwórz za pomocą...**  i wybierając polecenie **Edytor kodu źródłowego (tekst)**.

### <a name="to-edit-a-resource-script-file"></a>Aby edytować pliku skryptu zasobu

- Aby przekonwertować istniejącego pliku zasobów do szablonu, za pomocą pliku skryptu zasobu otwarty, w menu, przejdź do **pliku** > **Zapisz \< *filename*> jako**. Następnie określ lokalizację i wybierz polecenie **OK**.

Podczas tworzenia aplikacji Microsoft Foundation Class (MFC) dla Windows przy użyciu [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), Kreator generuje zestaw podstawowych plików w tym pliku zasobu skryptu (.rc)) zawiera podstawowe funkcje MFC. Jednak te funkcje specyficzne dla MFC nie są dostępne, edytując plik .rc dla aplikacji Windows, które nie są oparte na bibliotece MFC. W tym kreatorów kodu, ciągi menu podpowiedzi, zawartość list dla formantów pola kombi i formantu ActiveX.

- Aby dodać obsługę MFC z po otwarciu pliku skryptu zasobu w **widok zasobów**, wyróżnij folder zasobów (na przykład *MFC.rc*). Następnie w [okno właściwości](/visualstudio/ide/reference/properties-window)ustaw **tryb MFC** do **True**.

  > [!NOTE]
  > Oprócz ustawienia **tryb MFC**, plik .rc musi być częścią projektu MFC. Ustawienie tylko **tryb MFC** do **True** na .rc pliku w projekcie systemu Win32 nie daje funkcji MFC.

## <a name="create-resources"></a>Tworzenie zasobów

Można utworzyć zasobu, jako zasób domyślne czyli zasób, który nie jest oparty na szablonie, lub jako zasób deseniem po szablonu.

Użyj **widok zasobów** okno, aby wyświetlić pliki zasobów zawarte w swoich projektach. Rozwijanie folderu najwyższego poziomu, na przykład *Project1.rc*, zawiera typy zasobów, w tym pliku. Rozwiń każdego typu zasobu, aby wyświetlić poszczególne zasoby tego typu.

> [!TIP]
> Aby otworzyć **widok zasobów** okna, przejdź do menu **widoku** > **widok zasobów** lub naciśnij **Ctrl** +  **SHIFT**+**E**.

Kliknij prawym przyciskiem myszy można używać na **widok zasobów** okna do uruchamiania poleceń menu skrótów, lub kliknij dwukrotnie pasek tytułu, aby zadokować i oddokować okno. Kliknij prawym przyciskiem myszy pasek tytułu, aby uzyskać dodatkowe polecenia, które kontrolują zachowanie okna. Aby uzyskać więcej informacji, zobacz [zarządzania Windows](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

**Widok zasobów** system windows zawiera **Dodaj zasób** okno dialogowe z następującymi właściwościami, aby dodać zasoby do projektu aplikacji pulpitu Windows C++:

| Właściwość | Opis |
|---|---|
| **Typ zasobu** | Określ rodzaj zasobu, który chcesz utworzyć.<br/><br/>Można rozwinąć kursora i okna dialogowego pole zasobów kategorie, aby ujawnić dodatkowe zasoby, które znajdują się w programie Visual Studio ...\Microsoft \<wersji\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Jeśli potrzebujesz dodać .rct — pliki, umieść je w tym miejscu lub określić inny [ścieżki dołączania](../windows/how-to-specify-include-directories-for-resources.md).<br/><br/>Zasobów, jak pokazano na najwyższym poziomie w drzewie są zasoby domyślne, dostarczone przez program Visual Studio. Zasoby w plikach .rct są wyświetlane na drugim poziomie do odpowiedniej kategorii. Nie ma żadnych wstępnie limitu liczby .rct — pliki, które można dodać.<br/><br/> |
| **Nowy** | Utwórz zasób, w zależności od typu wybranego w **typ zasobu** pole, a następnie otwórz zasób w odpowiedniego edytora.<br/><br/>Na przykład, jeśli tworzysz zasobu okna dialogowego, zostanie ona otwarta zasobu w [Edytor okien dialogowych](../windows/dialog-editor.md). |
| **Importujuj** | Otwórz **zaimportować** okno dialogowe, przejdź do zasobu, który chcesz zaimportować do bieżącego projektu.<br/><br/>Możesz zaimportować mapy bitowej, ikony, kursor, HTML, dźwięku (. WAV) lub plik zasobów niestandardowych. |
| **Custom** | Otwórz **nowy niestandardowy zasób** okno dialogowe, aby utworzyć zasób niestandardowy.<br/><br/>Zawiera również **typ zasobu** właściwość, która zawiera pole tekstowe do wprowadzenia Nazwa typu zasobu niestandardowego. Visual C++ powoduje automatyczne rozpoczynanie nazwę podczas zamykania.<br/><br/>Zasoby niestandardowe są jedynie edytować w edytorze binarnym. |

Podczas tworzenia nowego zasobu, Visual C++ przypisze unikatową nazwę, na przykład `IDD_Dialog1`. Tego Identyfikatora zasobu można dostosować, edytując właściwości zasobu w edytorze skojarzonego zasobu lub w [okno właściwości](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> Określać nazwy zasobu lub identyfikator, który jest zarezerwowany przez program Visual Studio. Zarezerwowane nazwy to `DESIGNINFO`, `HWB`, i `TEXTINCLUDE`, a zarezerwowany identyfikator to `255`.

Aby utworzyć wykorzystanie zasobów, jedną z następujących czynności:

- W **widok zasobów**, wybierz swój plik .rc, a następnie użyć **Edytuj** > **Dodaj zasób** i wybierz typ zasobów do dodania do projektu.

   > [!TIP]
   > Również kliknięciu prawym przyciskiem myszy plik .rc w **widok zasobów** i wybierz polecenie **Dodaj zasób** z menu skrótów.

- W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy folder projektu, wybierz **Dodaj** > **Dodaj zasób** i wybierz typ zasobów do dodania do projektu.

   > [!NOTE]
   > Jeśli nie masz jeszcze pliku .rc w projekcie, ten krok spowoduje utworzenie jednego. Następnie możesz powtórzyć ten krok, aby dodać określonych typów zasobów do nowego pliku .rc.

- W [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy klasy, wybierz **Dodaj** > **Dodaj zasób** i wybierz typ zasobów do dodania do projektu.

- Użyj menu **projektu** > **Dodaj zasób**.

## <a name="use-resource-templates"></a>Użycie szablonów zasobów

Szablon zasobu jest dostosowane zasób, który został zapisany jako plik .rct. Szablonu usługi resource następnie służy jako punkt wyjścia do tworzenia zasobów. Szablony zasobów oszczędzić czas podczas opracowywania dodatkowe zasoby lub grupy zasobów, które udostępnianie funkcje, takie jak formanty standardowe lub powtarzające się elementy. Na przykład jeśli chcesz dołączyć przycisk Pomoc, za pomocą ikony logo firmy kilka okien dialogowych, Utwórz nowy szablon okno dialogowe i dostosować ją przy użyciu przycisku pomocy i logo.

Po dostosowaniu szablonu usługi resource, Zapisz zmiany w folderze szablonu lub w lokalizacji określonej w polu Ścieżka include, tak, że nowy szablon zasobu pojawią się w jego typ zasobu w **Dodaj zasób** okno dialogowe. Można teraz używać nowego szablonu zasobu tak często, zgodnie z potrzebami.

> [!NOTE]
> Edytor zasobów automatycznie zapewnia identyfikator unikatowy zasób Możesz poprawić [właściwości zasobu](../windows/changing-the-properties-of-a-resource.md) zgodnie z potrzebami.

> [!NOTE]
> Podkatalogi katalogu głównego szablonu, należy umieścić pliki szablonów specyficzne dla języka. Na przykład pliki szablonów angielskiej go w programie... \\< katalog szablonu zasobów\>\1033. Program Visual Studio wyszukuje nowe pliki .rct w programie Visual Studio \Program Files\Microsoft \<wersji\>\VC\VCResourceTemplates, \Program Files\Microsoft programu Visual Studio \<wersji > \VC\VCResourceTemplates\\< LCID\> (np. LCID 1033 dla języka angielskiego), lub w dowolnym miejscu [ścieżki dołączania](../windows/how-to-specify-include-directories-for-resources.md). Jeśli chcesz przechowywać pliki .rct w innej lokalizacji, należy dodać lokalizację do ścieżki dołączania.

### <a name="to-create-and-use-a-resource-template"></a>Tworzenie i używanie szablonu usługi resource

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt.

1. Z menu skrótów wybierz **Dodaj** > **Dodaj nowy element**.

1. W **szablonów:** okienku wybierz **plik szablonu zasobu (.rct)**.

1. Podaj nazwę i lokalizację nowego pliku .rct i wybierz pozycję **Otwórz**.

   Nowy plik .rct zostanie dodany do projektu i pojawia się w **Eksploratora rozwiązań** w obszarze **zasobów** folderu.

1. Kliknij dwukrotnie plik .rct, aby otworzyć go w oknie dokumentu. Aby dodać zasoby, kliknij prawym przyciskiem myszy plik w oknie dokumentu, a następnie wybierz **Dodaj zasób**.

   Można dostosować dodano zasobów i Zapisz plik .rct.

1. W **widok zasobów** okienku kliknij prawym przyciskiem myszy plik .rc i wybierz polecenie **Dodaj zasób**.

1. Wybierz znak plus (**+**) obok zasobu, aby rozwinąć węzeł zasobów i wyświetlić szablonów dostępnych dla tego zasobu.

1. Dwukrotnie kliknij szablon, który chcesz użyć.

   Dodano zasobów można zmodyfikować zgodnie z potrzebami w edytorze zasobów.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Instrukcje: Zarządzaj zasobami](../windows/how-to-copy-resources.md)<br/>
[Instrukcje: dołączanie zasobów w czasie kompilacji](../windows/how-to-include-resources-at-compile-time.md)<br/>