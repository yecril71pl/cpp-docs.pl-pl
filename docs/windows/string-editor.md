---
title: Edytor ciągów znaków (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.string.F1
- vc.editors.string
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
- strings [C++], searching
- strings [C++]
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: 24e4e6ba5b9c2dff1a179bea39830f4a3bbe5879
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702984"
---
# <a name="string-editor-c"></a>Edytor ciągów znaków (C++)

Tabela ciągów jest zasobem Windows, który zawiera listę identyfikatorów, wartości i podpisy dla wszystkich ciągów aplikacji. Na przykład monity pasek stanu znajdują się w tabeli ciągów.

Podczas tworzenia aplikacji, może mieć kilka tabel ciągów — jeden dla każdego języka lub warunku. Jednak modułowi wykonywalnemu ma tylko jedną tabelę ciągów. Uruchomionej aplikacji można odwoływać kilka tabel ciągów, jeżeli umieścisz tabel do różnych bibliotek DLL.

Tabele ciągów należy ułatwia lokalizowanie aplikacji w różnych językach. Jeśli wszystkie ciągi znajdują się w tabeli ciągów, można lokalizować aplikacji dzięki translacji ciągi (i inne zasoby) bez konieczności zmieniania kodu źródłowego. Ta sytuacja jest bardziej pożądane niż ręcznie Znajdowanie i zastępowanie różnych ciągów w plikach źródłowych.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych (projektów przeznaczonych dla środowiska uruchomieniowego języka wspólnego), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [instruktażu: Lokalizowanie formularzy Windows](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

Użyj **ciąg** edytor dla następujących czynności:

## <a name="to-find-a-string-resource-in-the-string-table"></a>Aby znaleźć zasobu ciągu w tabeli ciągów

Wyszukaj jeden lub więcej ciągów w tabeli ciągów i użyj [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) z **Znajdź w plikach** polecenia (**Edytuj** menu) aby znaleźć wszystkie wystąpienia ciągów które pasują do wzorca.

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Na **Edytuj** menu, wybierz opcję **Znajdź i Zamień**, następnie wybierz **znaleźć**.

1. W **Znajdź** Wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz podpis tekst lub identyfikator zasobu ciągu ma zostać odnaleziona.

1. Wybierz dowolny z **znaleźć** opcje.

1. Wybierz **Znajdź następny**.

   > [!TIP]
   > Aby użyć wyrażeń regularnych podczas wyszukiwania plików, należy użyć **Znajdź w plikach** polecenia. Typ wyrażenia regularnego pasują do wzorca, lub wybierz przycisk z prawej strony **Znajdź** pole, aby wyświetlić listę wyrażeń regularnych wyszukiwania. Po wybraniu wyrażenia z tej listy, zostanie zastąpiony jako wyszukiwany tekst w **Znajdź** pole. Upewnij się, jeśli używasz wyrażeń regularnych, **użyć: Wyrażenia regularne** pole wyboru jest zaznaczone.

## <a name="to-add-or-delete-a-string-resource"></a>Aby dodać lub usunąć zasób w postaci ciągu

Można szybko wstawiania lub usuwania wpisów do tabeli ciągów przy użyciu **ciąg** edytora. Nowych ciągów są umieszczane na końcu tabeli i podano następny dostępny identyfikator. Następnie można edytować **identyfikator**, **wartość**, lub **podpis** właściwości w [okno właściwości](/visualstudio/ide/reference/properties-window) zgodnie z potrzebami.

**Ciąg** edytora upewnia się, nie używaj Identyfikatora, który jest już używana. Wybranie Identyfikatora już w użyciu **ciąg** edytora zostanie powiadamiania o, a następnie przypisz ogólny Unikatowy identyfikator, na przykład `IDS_STRING58113`.

### <a name="to-add-a-string-table-entry"></a>Aby dodać wpis tabeli ciągów

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Kliknij prawym przyciskiem myszy w tabeli ciągów, a następnie wybierz **nowy ciąg** z menu skrótów.

1. W **ciąg** edytora, wybierz opcję **identyfikator** z listy rozwijanej identyfikator lub wpisz identyfikator bezpośrednio od razu.

1. Edytuj **wartość**, jeśli to konieczne.

1. Wpisz wpis dla **podpis**.

   > [!NOTE]
   > Ciągów o wartości null są niedozwolone w tabelach ciągów Windows. Jeśli tworzysz wpis w tabeli ciągów, który jest pusty ciąg, zostanie wyświetlony komunikat z prośbą do "Wprowadź ciąg dla tego wpisu w tabeli."

### <a name="to-delete-a-string-table-entry"></a>Aby usunąć wpis tabeli ciągów

1. Wybierz wpis, który chcesz usunąć.

1. Na **Edytuj** menu, wybierz opcję **Usuń**.

\- lub —

 Kliknij prawym przyciskiem myszy ciągu chcesz usunąć, a następnie wybierz **Usuń** z menu skrótów.

\- lub —

 Naciśnij klawisz **Usuń** klucza.

## <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Aby przenieść pliku skryptu zasobu w jeden ciąg

1. Otwórz w tabelach ciągów w obu plikach .rc. (Aby uzyskać więcej informacji, zobacz [wyświetlania zasobów w zasobu skryptu pliku poza z projektem](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Kliknij prawym przyciskiem myszy ciągu chcesz przenieść, a następnie wybierz **Wytnij** z menu skrótów.

1. Umieść kursor w miejscu docelowym **edytor ciągów** okna.

1. W pliku .rc, do którego chcesz przenieść ciągu, kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej** z menu skrótów.

   > [!NOTE]
   > Jeśli **identyfikator** lub **wartość** konfliktów ciągu przeniesione z istniejącym **identyfikator** lub **wartość** w pliku docelowym, albo **Identyfikator** lub **wartość** zmian przeniesionych ciągu. Jeśli ciąg istnieje z tym samym **identyfikator**, **identyfikator** zmian przeniesionych ciągu. Jeśli ciąg istnieje z tym samym **wartość**, **wartość** zmian przeniesionych ciągu.

## <a name="to-change-the-properties-of-a-string-resource"></a>Aby zmienić właściwości zasobu ciągu

Aby zmienić identyfikator, wartość oraz właściwości podpisu, można użyć edycji w miejscu.

### <a name="to-change-a-string-or-its-identifier"></a>Aby zmienić ciąg lub jego identyfikator.

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. Wybierz parametry chcesz edytować, a następnie kliknij dwukrotnie **identyfikator**, **wartość**, lub **podpis** kolumny. Teraz możesz wykonywać następujące czynności:

   - Wybierz **identyfikator** z **identyfikator listy rozwijanej** listy lub wpisz `ID` bezpośrednio w miejscu.

   - Wpisz inny numer w **wartość** kolumny.

   - Typ zmiany w **podpis** kolumny.

        > [!NOTE]
        >  Można również edytować właściwości ciągu w [okno właściwości](/visualstudio/ide/reference/properties-window).

### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Aby zmienić właściwości podpisu lub wielu zasobów ciągów

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Wybierz parametry, aby zmienić, przytrzymując **Ctrl** klucza, zgodnie z wybraniu każdej z nich.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), wpisz nową wartość dla właściwości, aby zmienić.

1. Naciśnij klawisz **wprowadź**.

## <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Aby dodać znaków specjalnych ani formatowania do zasobu ciągu

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Wybierz ciąg, który chcesz zmodyfikować.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), Dodaj dowolne sekwencje unikowe standardowych wymienionych poniżej, aby tekst w **podpis** pole i naciśnij klawisz **Enter**.

   |Aby uzyskać dostęp do tej|Wpisz to|
   |-----------------|---------------|
   | Nowy wiersz | \\n |
   | Powrót karetki | \\r |
   | Tab | \\t |
   | Ukośnik odwrotny (\\) | \\\\ |
   | Znak ASCII | \\ddd (Zapis ósemkowy) |
   | alert (dzwonek) | \\a |

> [!NOTE]
> **Ciąg** edytor nie obsługuje pełny zestaw znaki ucieczki przestają być ASCI. Można używać tylko wymienione powyżej.

> [!NOTE]
> Windows nie zezwala na tworzenie tabel pusty ciąg. Jeśli utworzysz tabeli ciągów z żadnych wpisów, zostanie usunięta automatycznie podczas zapisywania pliku zasobów.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Ciągi](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[Ciągi — informacje](/windows/desktop/menurc/about-strings)<br/>
[Dostosowywanie układów okien](/visualstudio/ide/customizing-window-layouts-in-visual-studio)