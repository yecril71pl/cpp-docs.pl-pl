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
ms.openlocfilehash: 996e5f132e5cfa33c39c4cc3ddbeb692f41925bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514712"
---
# <a name="string-editor-c"></a>Edytor ciągów (C++)

Tabela ciągów jest zasobem systemu Windows, który zawiera listę identyfikatorów, wartości i podpisów dla wszystkich ciągów aplikacji. Na przykład monity paska stanu znajdują się w tabeli ciągów.

Podczas tworzenia aplikacji można mieć kilka tabel ciągów — jeden dla każdego języka lub warunku. Jednak moduł wykonywalny ma tylko jedną tabelę ciągów. Działająca aplikacja może odwoływać się do kilku tabel ciągów, jeśli tabele są umieszczane w różnych bibliotekach DLL.

Tabele ciągów ułatwiają lokalizowanie aplikacji w różnych językach. Jeśli wszystkie ciągi znajdują się w tabeli ciągów, można zlokalizować aplikację przez przetłumaczenie ciągów (i innych zasobów) bez zmiany kodu źródłowego. Ta sytuacja jest bardziej pożądana niż ręczne Znajdowanie i zamienianie różnych ciągów w plikach źródłowych.

> [!NOTE]
> System Windows nie zezwala na tworzenie pustych tabel ciągów. Jeśli utworzysz tabelę ciągów bez wpisów, zostanie ona automatycznie usunięta podczas zapisywania pliku zasobów.

## <a name="how-to"></a>Instrukcje

**Edytor ciągów** umożliwia:

### <a name="to-find-a-string-resource-in-the-string-table"></a>Aby znaleźć zasób ciągu w tabeli ciągów

1. Otwórz tabelę ciągów przez dwukrotne kliknięcie jej ikony w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Przejdź do menu **Edycja** > **Znajdź i Zamień** i wybierz **Znajdź**.

1. W polu **Znajdź** , wybierz poprzedni ciąg wyszukiwania z listy rozwijanej lub wpisz tekst podpisu lub identyfikator zasobu ciągu, który ma zostać znaleziony.

1. Wybierz dowolną z opcji **Znajdź** i wybierz pozycję **Znajdź dalej**.

> [!TIP]
> Aby używać [wyrażeń regularnych](/visualstudio/ide/using-regular-expressions-in-visual-studio) podczas wyszukiwania plików, użyj polecenia **Znajdź w plikach** w menu **Edycja** .
>
> Wpisz wyrażenie regularne zgodne ze wzorcem lub wybierz przycisk z prawej strony pola **Znajdź** , aby wyświetlić listę zwykłych wyrażeń wyszukiwania. Po wybraniu wyrażenia z tej listy zostanie on zastąpiony jako tekst wyszukiwania w polu **Znajdź** .
>
> Jeśli używasz wyrażeń regularnych, upewnij się, że **używasz: Pole wyboru** wyrażenia regularne jest zaznaczone.

### <a name="to-add-or-delete-a-string-resource"></a>Aby dodać lub usunąć zasób ciągu

Można szybko wstawiać i usuwać wpisy w tabeli ciągów przy użyciu **edytora ciągów**. Nowe ciągi są umieszczane na końcu tabeli i otrzymują następny dostępny identyfikator. W razie konieczności można edytować właściwości **identyfikatora**, **wartości**lub **podpisu** w [okno właściwości](/visualstudio/ide/reference/properties-window) .

**Edytor ciągów** gwarantuje, że nie używasz identyfikatora, który jest już używany. Jeśli wybierzesz identyfikator, który jest już używany, **Edytor ciągów** wyświetli powiadomienie, a następnie przypisze ogólny unikatowy identyfikator, na `IDS_STRING58113`przykład.

#### <a name="to-add-a-string-table-entry"></a>Aby dodać wpis tabeli ciągów

1. Otwórz tabelę ciągów przez dwukrotne kliknięcie jej ikony w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Kliknij prawym przyciskiem myszy w tabeli ciągów i wybierz polecenie **Nowy ciąg**.

1. W **Edytorze ciągów**wybierz **Identyfikator** z listy rozwijanej **ID** lub wpisz *Identyfikator* bezpośrednio na miejscu.

1. W razie potrzeby edytuj **wartość**.

1. Wpisz wpis dla **podpisu**.

   > [!NOTE]
   > Ciągi o wartości null nie są dozwolone w tabelach ciągów systemu Windows. Jeśli utworzysz wpis w tabeli ciągów, który jest ciągiem o wartości null, zostanie wyświetlony komunikat z prośbą o **wprowadzenie ciągu dla tego wpisu w tabeli**.

#### <a name="to-delete-a-string-table-entry"></a>Aby usunąć wpis tabeli ciągów

Wybierz wpis, który chcesz usunąć, i wykonaj jedną z następujących czynności:

- Przejdź do menu **Edycja** > **Usuń**.

- Kliknij prawym przyciskiem myszy ciąg, który chcesz usunąć, a następnie wybierz polecenie **Usuń**.

- Naciśnij klawisz **delete** .

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Aby przenieść ciąg z jednego pliku skryptu zasobu do innego

1. [Otwórz tabele ciągów w obu plikach. RC](../windows/how-to-create-a-resource-script-file.md).

1. Kliknij prawym przyciskiem myszy ciąg, który chceszprzenieść, a następnie wybierz polecenie Wytnij.

1. Umieść kursor w oknie **edytora ciągu** docelowego.

1. W pliku *. RC* , do którego chcesz przenieść ciąg, kliknij prawym przyciskiem myszy i wybierz polecenie **Wklej**.

> [!NOTE]
> Jeśli **Identyfikator** lub **wartość** przenoszonego ciągu koliduje z istniejącym **identyfikatorem** lub **wartością** w pliku docelowym, to **Identyfikator** lub **wartość** przenoszonego ciągu zmienia się.

### <a name="to-change-the-properties-of-a-string-resource"></a>Aby zmienić właściwości zasobu ciągu

Aby zmienić właściwości **identyfikatora**, **wartości**i **podpisu** , można użyć edycji w miejscu.

> [!NOTE]
>  Możesz również edytować właściwości ciągu w [okno właściwości](/visualstudio/ide/reference/properties-window).

#### <a name="to-change-a-string-or-its-identifier"></a>Aby zmienić ciąg lub jego identyfikator

1. Otwórz tabelę ciągów przez dwukrotne kliknięcie jej ikony w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz ciąg, który chcesz edytować, a następnie kliknij dwukrotnie kolumnę **ID**, **Value**lub **Caption** . można:

   - Wybierz **Identyfikator** z listy rozwijanej **ID** lub wpisz *Identyfikator* bezpośrednio na miejscu.

   - Wpisz inną liczbę w kolumnie **wartość** .

   - Wpisz zmiany w kolumnie **Caption** .

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>Aby zmienić właściwość Caption dla wielu zasobów ciągów

1. Otwórz tabelę ciągów przez dwukrotne kliknięcie jej ikony w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz ciągi, które chcesz zmienić, przytrzymując wciśnięty klawisz **Ctrl** podczas zaznaczania każdego z nich.

1. W [oknie właściwości](/visualstudio/ide/reference/properties-window)wpisz nową wartość właściwości, którą chcesz zmienić.

1. Naciśnij klawisz **wprowadź**.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>Aby dodać formatowanie lub znaki specjalne do zasobu ciągu

1. Otwórz tabelę ciągów przez dwukrotne kliknięcie jej ikony w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz ciąg, który chcesz zmodyfikować.

1. W [oknie właściwości](/visualstudio/ide/reference/properties-window)Dodaj dowolne standardowe sekwencje ucieczki wymienione poniżej do tekstu w polu **podpis** i naciśnij klawisz **Enter**.

   |Aby to zrobić...|Wpisz to...|
   |-----------------|---------------|
   | Nowy wiersz | \\n |
   | Znak powrotu karetki | \\® |
   | Tab | \\t |
   | Ukośnik odwrotny\\() | \\\\ |
   | Znak ASCII | \\DDD (notacja ósemkowa) |
   | Alert (dzwonek) | \\a |

   > [!NOTE]
   > **Edytor ciągów** nie obsługuje pełnego zestawu ucieczki ASCI znaków. Można korzystać tylko z wymienionych powyżej.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[](../windows/resource-editors.md)
[Ciągi](/windows/win32/menurc/strings) edytorów zasobów<br/>
[Ciągi — informacje](/windows/win32/menurc/about-strings)<br/>
[Dostosowywanie układów okien](/visualstudio/ide/customizing-window-layouts-in-visual-studio)