---
title: Edytor ciągów (C++)
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
ms.openlocfilehash: b0fb077752cf1912e07175c68cdc8acfe758b0c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370237"
---
# <a name="string-editor-c"></a>Edytor ciągów (C++)

Tabela ciągów to zasób systemu Windows zawierający listę identyfikatorów, wartości i podpisów dla wszystkich ciągów aplikacji. Na przykład monity o pasek stanu znajdują się w tabeli ciągów.

Podczas tworzenia aplikacji, można mieć kilka tabel ciągów — po jednej dla każdego języka lub warunku. Jednak moduł wykonywalny ma tylko jedną tabelę ciągów. Uruchomiona aplikacja może odwoływać się do kilku tabel ciągów, jeśli umieścisz tabele w różnych bibliotekach DLL.

Tabele ciągów ułatwiają lokalizowanie aplikacji w różnych językach. Jeśli wszystkie ciągi znajdują się w tabeli ciągów, można zlokalizować aplikację, tłumacząc ciągi (i inne zasoby) bez zmiany kodu źródłowego. Ta sytuacja jest bardziej pożądane niż ręcznie znalezienie i zastąpienie różnych ciągów w plikach źródłowych.

> [!NOTE]
> System Windows nie zezwala na tworzenie pustych tabel ciągów. Jeśli utworzysz tabelę ciągów bez wpisów, zostanie ona automatycznie usunięta podczas zapisywania pliku zasobu.

## <a name="how-to"></a>Instrukcje

**Edytor ciągów** umożliwia:

### <a name="to-find-a-string-resource-in-the-string-table"></a>Aby znaleźć zasób ciągu w tabeli ciągów

1. Otwórz tabelę ciągów, klikając dwukrotnie jej ikonę w [widoku zasobu](how-to-create-a-resource-script-file.md#create-resources).

1. Przejdź do menu **Edytuj** > **znajdź i zamień** i wybierz pozycję **Znajdź**.

1. W polu **Znajdź, co** zaznacz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz tekst podpisu lub identyfikator zasobu ciągu, który chcesz znaleźć.

1. Wybierz dowolną z opcji **Znajdź** i wybierz pozycję **Znajdź następny**.

> [!TIP]
> Aby używać [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) podczas wyszukiwania plików, użyj polecenia **Znajdź w plikach** w menu **Edycja.**
>
> Wpisz wyrażenie regularne, aby dopasować go do wzorca, lub wybierz przycisk po prawej stronie pola **Znajdź, aby** wyświetlić listę wyrażeń wyszukiwania regularnego. Po wybraniu wyrażenia z tej listy jest ono zastępowane jako tekst wyszukiwania w polu **Znajdź, co.**
>
> Jeśli używasz wyrażeń regularnych, upewnij się, że pole wyboru Użyj: Wyrażenia regularne jest **zaznaczone.**

### <a name="to-add-or-delete-a-string-resource"></a>Aby dodać lub usunąć zasób ciągu

Można szybko wstawiać lub usuwać wpisy do tabeli ciągów za pomocą **Edytora ciągów**. Nowe ciągi są umieszczane na końcu tabeli i otrzymują następny dostępny identyfikator. W razie potrzeby można edytować właściwości **Identyfikator,** **Wartość**lub **Podpis** w [oknie Właściwości.](/visualstudio/ide/reference/properties-window)

**Edytor ciągów** zapewnia, że nie używasz identyfikatora, który jest już używany. Jeśli wybierzesz identyfikator już używany, **Edytor ciągów** powiadomi Cię, a następnie `IDS_STRING58113`przypisze ogólny unikatowy identyfikator, na przykład .

#### <a name="to-add-a-string-table-entry"></a>Aby dodać wpis tabeli ciągów

1. Otwórz tabelę ciągów, klikając dwukrotnie jej ikonę w [widoku zasobu](how-to-create-a-resource-script-file.md#create-resources).

1. Kliknij prawym przyciskiem myszy tabelę ciągów i wybierz polecenie **Nowy ciąg**.

1. W **Edytorze ciągów**wybierz **identyfikator** z listy rozwijanej **Identyfikator** lub wpisz *identyfikator* bezpośrednio na miejscu.

1. W razie potrzeby edytuj **wartość.**

1. Wpisz wpis dla **podpisu**.

   > [!NOTE]
   > Ciągi null nie są dozwolone w tabelach ciągów systemu Windows. Jeśli utworzysz wpis w tabeli ciągów, który jest ciągiem zerowym, otrzymasz wiadomość z **prośbą o wprowadzenie ciągu dla tego wpisu tabeli**.

#### <a name="to-delete-a-string-table-entry"></a>Aby usunąć wpis tabeli ciągów

Zaznacz wpis, który chcesz usunąć, i wykonaj jedną z następujących czynności:

- Przejdź do menu **Edytuj** > **usuń**.

- Kliknij prawym przyciskiem myszy ciąg, aby usunąć, a następnie wybierz polecenie **Usuń**.

- Naciśnij klawisz **Delete.**

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Aby przenieść ciąg z jednego pliku skryptu zasobu do innego

1. [Otwórz tabele ciągów w obu plikach .rc](../windows/how-to-create-a-resource-script-file.md).

1. Kliknij prawym przyciskiem myszy ciąg, aby przenieść i wybierz polecenie **Wytnij**.

1. Umieść kursor w docelowym oknie **Edytora ciągów.**

1. W pliku *rc,* do którego chcesz przenieść ciąg, kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej**.

> [!NOTE]
> Jeśli **identyfikator** lub **wartość** przeniesionego ciągu powoduje konflikt z istniejącym **identyfikatorem** lub **wartością** w pliku docelowym, zmieni **się ten identyfikator** lub **wartość** przeniesionego ciągu.

### <a name="to-change-the-properties-of-a-string-resource"></a>Aby zmienić właściwości zasobu ciągu

Za pomocą edycji w miejscu można zmienić właściwości **Identyfikator**, **Wartość**i **Podpis.**

> [!NOTE]
> Można również edytować właściwości ciągu w [oknie Właściwości](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-a-string-or-its-identifier"></a>Aby zmienić ciąg lub jego identyfikator

1. Otwórz tabelę ciągów, klikając dwukrotnie jej ikonę w [widoku zasobu](how-to-create-a-resource-script-file.md#create-resources).

1. Zaznacz ciąg, który chcesz edytować, i kliknij dwukrotnie kolumnę **ID**, **Value**lub **Caption,** a następnie możesz:

   - Wybierz **identyfikator** z listy rozwijanej **Identyfikator** lub wpisz *identyfikator* bezpośrednio na miejscu.

   - Wpisz inną liczbę w kolumnie **Wartość.**

   - Wpisz zmiany w kolumnie **Podpis.**

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Aby zmienić właściwość podpisu wielu zasobów ciągów

1. Otwórz tabelę ciągów, klikając dwukrotnie jej ikonę w [widoku zasobu](how-to-create-a-resource-script-file.md#create-resources).

1. Zaznacz ciągi, które chcesz zmienić, przytrzymując klawisz **Ctrl** podczas wybierania każdego z nich.

1. W [oknie Właściwości](/visualstudio/ide/reference/properties-window)wpisz nową wartość właściwości, którą chcesz zmienić.

1. Naciśnij **klawisz Enter**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Aby dodać formatowanie lub znaki specjalne do zasobu ciągu

1. Otwórz tabelę ciągów, klikając dwukrotnie jej ikonę w [widoku zasobu](how-to-create-a-resource-script-file.md#create-resources).

1. Zaznacz ciąg, który chcesz zmodyfikować.

1. W [oknie Właściwości](/visualstudio/ide/reference/properties-window)dodaj dowolną ze standardowych sekwencji unikowych wymienionych poniżej do tekstu w polu **Podpis** i naciśnij **klawisz Enter**.

   |Aby to uzyskać...|Wpisz to...|
   |-----------------|---------------|
   | Nowa linia | \\N |
   | Powrót karetki | \\R |
   | Tab | \\t |
   | Ukośnik\\odwrotny ( ) | \\\\ |
   | Znak ASCII | \\ddd (notacja ósemka) |
   | Alert (dzwonek) | \\A |

   > [!NOTE]
   > **Edytor ciągów** nie obsługuje pełnego zestawu znaków ASCI ze strony asci. Możesz używać tylko tych wymienionych powyżej.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Ciągi edytorów](../windows/resource-editors.md)
[zasobów](/windows/win32/menurc/strings)<br/>
[Informacje o ciągach](/windows/win32/menurc/about-strings)<br/>
[Dostosowywanie układów okien](/visualstudio/ide/customizing-window-layouts-in-visual-studio)
