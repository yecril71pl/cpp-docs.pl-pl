---
title: Edytor ciągów znaków (C++)
ms.date: 02/14/2019
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
ms.openlocfilehash: 47d5835356863383b32baffc4475e01a652e9856
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037188"
---
# <a name="string-editor-c"></a>Edytor ciągów znaków (C++)

Tabela ciągów jest zasobem Windows, który zawiera listę identyfikatorów, wartości i podpisy dla wszystkich ciągów aplikacji. Na przykład monity pasek stanu znajdują się w tabeli ciągów.

Podczas tworzenia aplikacji, może mieć kilka tabel ciągów — jeden dla każdego języka lub warunku. Jednak modułowi wykonywalnemu ma tylko jedną tabelę ciągów. Uruchomionej aplikacji można odwoływać kilka tabel ciągów, jeżeli umieścisz tabel do różnych bibliotek DLL.

Tabele ciągów należy ułatwia lokalizowanie aplikacji w różnych językach. Jeśli wszystkie ciągi znajdują się w tabeli ciągów, można lokalizować aplikacji dzięki translacji ciągi (i inne zasoby) bez konieczności zmieniania kodu źródłowego. Ta sytuacja jest bardziej pożądane niż ręcznie Znajdowanie i zastępowanie różnych ciągów w plikach źródłowych.

> [!NOTE]
> Windows nie zezwala na tworzenie tabel pusty ciąg. Jeśli utworzysz tabeli ciągów z żadnych wpisów, zostanie usunięta automatycznie podczas zapisywania pliku zasobów.

## <a name="how-to"></a>Instrukcje

**Edytor ciągów** umożliwia:

### <a name="to-find-a-string-resource-in-the-string-table"></a>Aby znaleźć zasobu ciągu w tabeli ciągów

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Przejdź do menu **Edytuj** > **Znajdź i Zamień** i wybierz polecenie **znaleźć**.

1. W **Znajdź** pole, wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz podpis tekst lub identyfikator zasobu ciągu ma zostać odnaleziona.

1. Wybierz dowolny z **znaleźć** opcje, a następnie wybierz **Znajdź następny**.

> [!TIP]
> Aby użyć [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) podczas wyszukiwania plików, użyj **Znajdź w plikach** polecenia w pliku **Edytuj** menu.
>
> Typ wyrażenia regularnego pasują do wzorca, lub wybierz przycisk z prawej strony **Znajdź** pole, aby wyświetlić listę wyrażeń regularnych wyszukiwania. Po wybraniu wyrażenia z tej listy, zostanie zastąpiony jako wyszukiwany tekst w **Znajdź** pole.
>
> Upewnij się, jeśli używasz wyrażeń regularnych, **użyć: Wyrażenia regularne** pole wyboru jest zaznaczone.

### <a name="to-add-or-delete-a-string-resource"></a>Aby dodać lub usunąć zasób w postaci ciągu

Można szybko wstawiania lub usuwania wpisów do tabeli ciągów przy użyciu **edytor ciągów**. Nowych ciągów są umieszczane na końcu tabeli i podano następny dostępny identyfikator. Możesz edytować **identyfikator**, **wartość**, lub **podpis** właściwości w [okno właściwości](/visualstudio/ide/reference/properties-window) zgodnie z potrzebami.

**Edytor ciągów** upewnia się, nie używaj Identyfikatora, który jest już używana. Wybranie Identyfikatora już w użyciu **edytor ciągów** o, a następnie przypisz ogólny Unikatowy identyfikator, na przykład `IDS_STRING58113`.

#### <a name="to-add-a-string-table-entry"></a>Aby dodać wpis tabeli ciągów

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Kliknij prawym przyciskiem myszy w tabeli ciągów, a następnie wybierz **nowy ciąg**.

1. W **edytor ciągów**, wybierz opcję **identyfikator** z **identyfikator** listy rozwijanej lub wpisz *identyfikator* bezpośrednio w miejscu.

1. Edytuj **wartość**, jeśli to konieczne.

1. Wpisz wpis dla **podpis**.

   > [!NOTE]
   > Ciągów o wartości null nie są dozwolone w tabelach ciągów Windows. Jeśli utworzysz wpis w tabeli ciągów, który jest pusty ciąg, otrzymasz komunikat z prośbą o **wprowadź ciąg dla tego wpisu w tabeli**.

#### <a name="to-delete-a-string-table-entry"></a>Aby usunąć wpis tabeli ciągów

Wybierz wpis, który chcesz usunąć, a następnie wykonaj jedną z następujących czynności:

- Przejdź do menu **Edytuj** > **Usuń**.

- Kliknij prawym przyciskiem myszy ciąg do usunięcia i wybierz **Usuń**.

- Naciśnij klawisz **Usuń** klucza.

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Aby przenieść pliku skryptu zasobu w jeden ciąg

1. [Otwieranie tabel ciągów w obu plikach .rc](../windows/how-to-create-a-resource-script-file.md).

1. Kliknij prawym przyciskiem myszy ciągu i wybierz polecenie **Wytnij**.

1. Umieść kursor w miejscu docelowym **edytor ciągów** okna.

1. W *.rc* pliku, do której chcesz przenieść ciągu, kliknij prawym przyciskiem myszy i wybierz **Wklej**.

> [!NOTE]
> Jeśli **identyfikator** lub **wartość** konfliktów ciągu przeniesione z istniejącym **identyfikator** lub **wartość** w pliku docelowym, albo że **Identyfikator** lub **wartość** zmian przeniesionych ciągu.

### <a name="to-change-the-properties-of-a-string-resource"></a>Aby zmienić właściwości zasobu ciągu

Umożliwia edycję w miejscu zmienić **identyfikator**, **wartość**, i **podpis** właściwości.

> [!NOTE]
>  Można również edytować właściwości ciągu w [okno właściwości](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-a-string-or-its-identifier"></a>Aby zmienić ciąg lub jego identyfikator.

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz parametry chcesz edytować, a następnie kliknij dwukrotnie ikonę **identyfikator**, **wartość**, lub **podpis** kolumny, a następnie użytkownik może:

   - Wybierz **identyfikator** z **identyfikator** listy rozwijanej lub wpisz *identyfikator* bezpośrednio w miejscu.

   - Wpisz inny numer w **wartość** kolumny.

   - Typ zmiany w **podpis** kolumny.

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Aby zmienić właściwości podpisu lub wielu zasobów ciągów

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz parametry, aby zmienić, przytrzymując **Ctrl** klucza, zgodnie z wybraniu każdej z nich.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), wpisz nową wartość dla właściwości, aby zmienić.

1. Naciśnij klawisz **wprowadź**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Aby dodać znaków specjalnych ani formatowania do zasobu ciągu

1. Otwórz tabeli ciągów, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz ciąg, który chcesz zmodyfikować.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), Dodaj dowolne sekwencje unikowe standardowych wymienionych poniżej, aby tekst w **podpis** pole i naciśnij klawisz **Enter**.

   |Aby uzyskać dostęp do tej...|Wpisz to...|
   |-----------------|---------------|
   | Nowy wiersz | \\n |
   | Powrót karetki | \\r |
   | Tab | \\t |
   | Ukośnik odwrotny (\\) | \\\\ |
   | Znak ASCII | \\ddd (Zapis ósemkowy) |
   | alert (dzwonek) | \\a |

   > [!NOTE]
   > **Edytor ciągów** nie obsługuje ona pełnego zestawu znaki ucieczki przestają być ASCI. Można używać tylko wymienione powyżej.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)
<!--
[Strings](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[About Strings](/windows/desktop/menurc/about-strings)<br/>
[Customizing window layouts](/visualstudio/ide/customizing-window-layouts-in-visual-studio)-->