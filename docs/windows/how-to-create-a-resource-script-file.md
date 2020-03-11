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
ms.openlocfilehash: c997c7a1b2d7fb3a852a42fa78faf2be6074705e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866124"
---
# <a name="how-to-create-resources-c"></a>Instrukcje: Tworzenie zasobów (C++)

Zasoby dla projektu można tworzyć według:

- Przy użyciu pliku skryptu zasobu.

   > [!NOTE]
   > Ten krok jest niezbędny przed dodaniem zasobów.

- Dodawanie zasobów do projektu i korzystanie z **Widok zasobów**.

- Tworzenie niestandardowych zasobów przy użyciu szablonu zasobu.

## <a name="use-resource-script-files"></a>Korzystanie z plików skryptów zasobów

Przed utworzeniem i dodaniem nowych zasobów do projektu należy najpierw utworzyć plik skryptu zasobu (. RC).

> [!NOTE]
> Plik skryptu zasobu można dodać tylko do istniejącego projektu załadowanego do środowiska IDE programu Visual Studio. Nie można utworzyć autonomicznego skryptu zasobu poza projektem, ale pliki szablonu zasobów (. rct) można utworzyć w dowolnym momencie.

### <a name="to-create-a-resource-script-file"></a>Aby utworzyć plik skryptu zasobu

1. Umieść fokus w istniejącym folderze projektu w **Eksplorator rozwiązań**, na przykład, *WebProject*.

   > [!NOTE]
   > Nie należy mylić folderu projektu z folderem rozwiązania w **Eksplorator rozwiązań**. Jeśli umieścisz fokus w folderze **rozwiązania** , nie będziesz mieć tego samego wyboru **Dodaj nowy element** .

1. W menu Przejdź do pozycji **Project** > **Dodaj nowy element**.

1. Wybierz folder **wizualizacji C++**  i wybierz pozycję **plik zasobów (. RC)** w okienku po prawej stronie.

1. Podaj nazwę pliku skryptu zasobu w polu tekstowym **Nazwa** , a następnie wybierz pozycję **Otwórz**.

### <a name="to-open-a-resource-script-file"></a>Aby otworzyć plik skryptu zasobu

Zasoby można wyświetlić w pliku skryptu zasobu bez otwartego projektu. Plik skryptu zostanie otwarty w oknie dokumentu, w przeciwieństwie do **Widok zasobów**.

> [!NOTE]
> Niektóre polecenia są dostępne tylko wtedy, gdy plik jest otwarty autonomicznie, co oznacza poza projektem bez uprzedniego załadowania projektu. Na przykład, aby użyć polecenia **Zapisz jako** i zapisać plik o innym formacie lub nazwie pliku, plik musi być otwarty autonomicznie.

- Aby otworzyć plik skryptu zasobu poza projektem, w menu Przejdź do **pliku** > **Otwórz**, a następnie wybierz **plik**. Przejdź do pliku skryptu zasobu, zaznacz plik i wybierz polecenie **Otwórz**.

    > [!NOTE]
    > Mogą wystąpić sytuacje, w których chcesz wyświetlić zawartość pliku skryptu zasobu projektu bez używania edytorów zasobów, aby otworzyć zasób. Na przykład można wyszukać ciąg we wszystkich oknach dialogowych w pliku zasobów bez konieczności oddzielnego otwierania każdego z nich. Możesz łatwo otworzyć plik zasobów w formacie tekstowym, aby wyświetlić wszystkie zawarte w nim zasoby i zakończyć operacje globalne obsługiwane przez Edytor tekstu.
    >
    > Aby otworzyć plik skryptu zasobu w formacie tekstowym, użyj strzałki listy rozwijanej po prawej stronie przycisku **Otwórz** w powyższym kroku, a następnie wybierz **Otwórz za pomocą**. Wybierz pozycję **Edytor kodu źródłowego (tekst)** , a następnie z listy rozwijanej **Otwórz jako** wybierz pozycję **tekst** , a zasób zostanie otwarty w edytorze **kodu źródłowego** .

- Aby otworzyć wiele skryptów zasobów, wykonaj te same czynności dla każdego pliku, który chcesz otworzyć, na przykład *Source1. RC* i *SOURCE2. RC*. Następnie, gdy oba pliki. RC są otwarte w osobnych dokumentach systemu Windows, użyj menu **okno** lub kliknij prawym przyciskiem myszy jeden z plików, a następnie wybierz pozycję **Nowa pozioma Grupa kart** lub **Nowa pionowa Grupa kart**. Okna są teraz sąsiadujące, aby można było je przeglądać jednocześnie.

> [!TIP]
> Pliki skryptów zasobów można otworzyć, klikając prawym przyciskiem myszy plik. RC w **Eksplorator rozwiązań**, wybierając polecenie **Otwórz za pomocą** i wybierając **Edytor kodu źródłowego (tekst)** .

Podczas kompilowania aplikacji Microsoft Foundation Class (MFC) dla systemu Windows za pomocą [Kreatora aplikacji MFC](../mfc/reference/mfc-application-wizard.md)Kreator generuje podstawowy zestaw plików, w tym plik skryptu zasobu (. RC), który zawiera podstawowe funkcje MFC. Jednak te funkcje specyficzne dla MFC nie są dostępne podczas edytowania pliku. RC dla aplikacji systemu Windows, które nie są oparte na MFC. Obejmuje to kreatory kodu, ciągi poleceń menu, zawartość listy dla kontrolek pola kombi i hostingu formantów ActiveX.

- Aby dodać obsługę MFC, przy otwartym pliku skryptu zasobu w **Widok zasobów**zaznacz folder zasoby (na przykład *MFC. RC*). Następnie w [okno właściwości](/visualstudio/ide/reference/properties-window)ustawić **wartość true**dla **trybu MFC** .

  > [!NOTE]
  > Oprócz ustawiania **trybu MFC**plik. RC musi być częścią projektu MFC. Tylko **Tryb MFC** o **wartości true** w pliku. RC w projekcie Win32 nie udostępnia funkcji MFC.

## <a name="create-resources"></a>Tworzenie zasobów

Zasób można utworzyć jako nowy zasób domyślny, co oznacza, że zasób, który nie jest oparty na szablonie, lub jako zasób, który jest zadany przy użyciu szablonu.

Użyj okna **Widok zasobów** , aby wyświetlić pliki zasobów zawarte w projektach. Rozszerzenie folderu najwyższego poziomu, na przykład *Project1. RC*, pokazuje typy zasobów w tym pliku. Rozwiń każdy typ zasobu, aby wyświetlić poszczególne zasoby tego typu.

> [!TIP]
> Aby otworzyć okno **Widok zasobów** , przejdź do **widoku** menu, > **inne Windows** > **Widok zasobów** lub naciśnij klawisz **Ctrl**+**SHIFT**+**E**.

Możesz również kliknąć prawym przyciskiem myszy okno **Widok zasobów** , aby uruchomić menu skrótów poleceń, lub dwukrotnie kliknąć pasek tytułu, aby zadokować i oddokować okno. Kliknij prawym przyciskiem myszy pasek tytułu poleceń kontrolujących zachowanie okna. Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

**Widok zasobów** okna zawiera okno dialogowe **Dodawanie zasobu** z następującymi właściwościami, aby dodać zasoby do projektu aplikacji C++ klasycznej systemu Windows:

| Właściwość | Opis |
|---|---|
| **Typ zasobu** | Określ rodzaj zasobu, który chcesz utworzyć.<br/><br/>Można rozwinąć kategorie zasobów kursora i okna dialogowego, aby odsłonić dodatkowe zasoby, które znajdują się w *. \Microsoft Visual Studio \<wersja\>\VC\VCResourceTemplates\\< LCID\>\mfc.RCT*. Jeśli musisz dodać pliki. rct, umieść je w tym miejscu lub określ inną [ścieżkę include](../windows/how-to-specify-include-directories-for-resources.md). Zasoby wyświetlane na najwyższym poziomie w formancie drzewa są domyślnymi zasobami udostępnianymi przez program Visual Studio. Zasoby w plikach. RCT są wyświetlane na drugim poziomie w odpowiedniej kategorii. Brak wstępnie zdefiniowanego limitu liczby plików. rct, które można dodać.<br/><br/> |
| **Nowy** | Utwórz zasób oparty na typie wybranym w polu **Typ zasobu** i Otwórz zasób w odpowiednim edytorze.<br/><br/>Na przykład w przypadku utworzenia zasobu okna dialogowego otwiera on zasób w [edytorze okien dialogowych](../windows/dialog-editor.md). |
| **Importujuj** | Otwórz okno dialogowe **Importuj** , aby przejść do zasobu, który ma zostać zaimportowany do bieżącego projektu.<br/><br/>Możesz zaimportować mapę bitową, ikonę, kursor, kod HTML, dźwięk (. WAV) lub niestandardowy plik zasobów. |
| **Niestandardowy** | Otwórz okno dialogowe **nowy zasób niestandardowy** , aby utworzyć zasób niestandardowy.<br/><br/>Zawiera również właściwość **typu zasobu** , która zawiera pole tekstowe służące do wprowadzania nazwy niestandardowego typu zasobu. Wizualizacja C++ jest automatycznie zamieniana na wielką nazwę po zakończeniu. Zasoby niestandardowe są edytowane tylko w [edytorze binarnym](../windows/binary-editor.md). |

Podczas tworzenia nowego zasobu, Visual C++ przypisuje do niego unikatową nazwę, na przykład `IDD_Dialog1`. Ten identyfikator zasobu można dostosować, edytując właściwości zasobu w odpowiednim edytorze zasobów lub w [okno właściwości](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> Nie określaj nazwy lub identyfikatora zasobu, który jest zarezerwowany przez program Visual Studio. Zarezerwowane nazwy to `DESIGNINFO`, `HWB`i `TEXTINCLUDE`, a zarezerwowany identyfikator to `255`.

### <a name="to-create-a-resource"></a>Aby utworzyć zasób

- W **Widok zasobów**wybierz plik. RC, a następnie użyj polecenia **Edytuj** > **Dodaj zasób** i wybierz typ zasobu, który ma zostać dodany do projektu.

   > [!TIP]
   > Możesz również kliknąć prawym przyciskiem myszy plik. RC w **Widok zasobów** i wybrać polecenie **Dodaj zasób** z menu skrótów.

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder projektu, wybierz polecenie **Dodaj** > **Dodaj zasób** i wybierz typ zasobu, który ma zostać dodany do projektu.

   > [!NOTE]
   > Jeśli nie masz jeszcze pliku. RC w projekcie, ten krok zostanie utworzony. Następnie można powtórzyć ten krok, aby dodać określone typy zasobów do nowego pliku. rc.

- W [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code)kliknij prawym przyciskiem myszy klasę, wybierz pozycję **Dodaj** > **Dodaj zasób** i wybierz typ zasobu, który ma zostać dodany do projektu.

- Użyj **projektu** menu > **Dodaj zasób**.

## <a name="use-resource-templates"></a>Korzystanie z szablonów zasobów

Szablon zasobu to dostosowany zasób zapisany jako plik. RCT. Następnie szablon zasobu służy jako punkt wyjścia do tworzenia zasobów. Szablony zasobów oszczędzają czas podczas opracowywania dodatkowych zasobów lub grup zasobów, które współużytkują funkcje, takie jak formanty standardowe lub powtarzalne elementy. Jeśli na przykład chcesz dołączyć przycisk pomocy z ikoną logo firmy w kilku oknach dialogowych, Utwórz nowy szablon okna dialogowego i dostosuj go za pomocą przycisku Pomoc i logo.

Po dostosowaniu szablonu zasobu Zapisz zmiany w folderze szablonu lub w lokalizacji określonej w ścieżce dołączania, tak aby nowy szablon zasobu pojawił się w obszarze Typ zasobu w oknie dialogowym **Dodaj zasób** . Teraz możesz użyć nowego szablonu zasobu tak często, jak jest to konieczne.

> [!NOTE]
> Edytor zasobów automatycznie zapewnia unikatowy identyfikator zasobu. W razie konieczności można skorygować [właściwości zasobów](../windows/changing-the-properties-of-a-resource.md) .

> [!NOTE]
> Umieść pliki szablonów charakterystyczne dla języka w podkatalogach katalogu głównego szablonu. Na przykład pliki szablonów tylko w języku angielskim można znaleźć w *..\\< katalogu szablonów zasobów\>\ 1033*.
>
> Program Visual Studio wyszukuje nowe pliki. RCT w *folderze \Program Files\Microsoft Visual studio \<wersja\>\VC\VCResourceTemplates*, *\Program files\microsoft Visual Studio \<version > \VC\VCRESOURCETEMPLATES\\< LCID\>* (na przykład LCID 1033 dla języka angielskiego) lub w dowolnym miejscu na [ścieżce dołączania](../windows/how-to-specify-include-directories-for-resources.md). Jeśli wolisz przechowywać pliki. RCT w innej lokalizacji, musisz dodać lokalizację do ścieżki dołączania.

### <a name="to-create-and-use-a-resource-template"></a>Tworzenie i używanie szablonu zasobów

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Dodaj** > **Dodaj nowy element**.

1. W okienku **Szablony:** wybierz pozycję **plik szablonu zasobu (. rct)** .

1. Podaj nazwę i lokalizację nowego pliku *. RCT* , a następnie wybierz pozycję **Otwórz**.

   Nowy plik *. RCT* jest dodawany do projektu i pojawia się w **Eksplorator rozwiązań** w folderze **resources** .

1. Kliknij dwukrotnie plik *. RCT* , aby otworzyć go w oknie dokumentu. Aby dodać zasoby, kliknij prawym przyciskiem myszy plik w oknie dokumentu i wybierz polecenie **Dodaj zasób**.

   Możesz dostosować dodane zasoby i zapisać plik *. RCT* .

1. W okienku **Widok zasobów** kliknij prawym przyciskiem myszy plik *. RC* , a następnie wybierz polecenie **Dodaj zasób**.

1. Wybierz znak plus ( **+** ) obok zasobu, aby rozwinąć węzeł zasobów i wyświetlić szablony dostępne dla tego zasobu.

1. Kliknij dwukrotnie szablon, którego chcesz użyć.

   Dodany zasób można zmodyfikować zgodnie z wymaganiami w jego edytorze zasobów.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>Aby skonwertować istniejący plik zasobów do szablonu

Po otwarciu pliku skryptu zasobu w menu Przejdź do **pliku** > **zapisz \<*filename*> jako**. Określ lokalizację i wybierz **przycisk OK**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Instrukcje: zarządzanie zasobami](../windows/how-to-copy-resources.md)<br/>
[Instrukcje: dołączanie zasobów w czasie kompilacji](../windows/how-to-include-resources-at-compile-time.md)<br/>