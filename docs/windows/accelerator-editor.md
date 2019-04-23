---
title: Edytor klawiszy skrótów (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator.F1
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: f5ae9880719a3a8b799ea8deb751b6f0a85542bd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041127"
---
# <a name="accelerator-editor-c"></a>Edytor klawiszy skrótów (C++)

Tabeli klawiszy skrótu jest zasobem Windows C++, który zawiera listę klawiszy skrótów, znane jako klawisze skrótów i identyfikatory poleceń, które są skojarzone z nimi. Program może mieć więcej niż jednej tabeli akceleratora.

Zwykle akceleratorów są używane jako skróty klawiaturowe dla poleceń programu, które są również dostępne w menu lub paska narzędzi. Jednak można użyć tabeli akceleratora do definiowania kombinacji klawiszy dla polecenia, które nie mają skojarzonych z nimi obiektu interfejsu użytkownika.

> [!TIP]
> Korzystając z **Edytor klawiszy skrótów**, kliknij prawym przyciskiem myszy, aby wyświetlić menu skrótów częste poleceń. Dostępne polecenia zależą od tego, wskaźnik wskazuje na.

Możesz użyć [Widok klas](/visualstudio/ide/viewing-the-structure-of-code) można dołączyć klucza polecenia klawiszy skrótów do kodu. Aby uzyskać listę predefiniowanych klawiszy skrótów, zobacz [klawiszy](../windows/predefined-accelerator-keys.md).

> [!NOTE]
> Windows nie zezwala na tworzenie tabel akceleratora puste. Jeśli utworzenia tabeli akceleratora żadnych wpisów, zostanie usunięta automatycznie po zapisaniu tabeli.

## <a name="accelerator-properties"></a>Właściwości klawiszy skrótów

Można ustawić właściwości klawiszy skrótów w [okno właściwości](/visualstudio/ide/reference/properties-window) w dowolnym momencie. Można również użyć **Edytor klawiszy skrótów** do modyfikowania właściwości klawiszy skrótów w tabeli klawiszy skrótu. Zmiany wprowadzone przy użyciu **właściwości** okna lub **Edytor klawiszy skrótów** mają ten sam wynik, zmiany są natychmiast odzwierciedlane w tabeli klawiszy skrótu.

**Identyfikator** właściwości odwołuje się do każdego wpisu tabeli akceleratora w kodzie programu. Ten wpis jest wartość polecenie odbierająca po naciśnięciu klawisza skrótu lub kombinację klawiszy. Aby akceleratora taki sam jak element menu, upewnij **identyfikator** takie same, tak długo, jak **identyfikator** akceleratora tabeli jest taka sama jak **identyfikator** zasobu menu.

Każdy akcelerator **identyfikator** ma trzy właściwości: **Modyfikator**, **klucz**, i **typu**

**Modyfikator** właściwość ustawia kontroli kombinacje klawiszy dla akceleratora.

> [!NOTE]
> W **właściwości** oknie **modyfikator** właściwość pojawia się jako trzy osobne **logiczna** właściwości, które mogą być kontrolowane niezależnie: **ALT**, **Ctrl**, i **Shift**.

Poniżej znajdują się wpisy prawne **modyfikator** właściwości w tabeli akceleratora:

   |Wartość|Opis|
   |-----------|-----------------|
   |**Brak**|Użytkownik naciśnie tylko **klucz** wartość.<br/><br/>Ta wartość jest najbardziej efektywne używana przy użyciu wartości ASCII/ANSI 001 za pośrednictwem 026, który jest interpretowany jako ^ od A do ^ Z (**Ctrl + A** za pośrednictwem **Ctrl + Z**).|
   |**ALT**|Użytkownik musi nacisnąć klawisz **Alt** przed **klucz** wartość.|
   |**Ctrl**|Użytkownik musi nacisnąć klawisz **Ctrl** przed **klucz** wartość nie jest prawidłowy z typem ASCII.|
   |**SHIFT**|Użytkownik musi nacisnąć klawisz **Shift** przed **klucz** wartość.|
   |**Ctrl+Alt**|Użytkownik musi nacisnąć klawisz **Ctrl** i **Alt** przed **klucz** wartość nie jest prawidłowy z typem ASCII.|
   |**Ctrl+Shift**|Użytkownik musi nacisnąć klawisz **Ctrl** i **Shift** przed **klucz** wartość nie jest prawidłowy z typem ASCII.|
   |**Alt+Shift**|Użytkownik musi nacisnąć klawisz **Alt** i **Shift** przed **klucz** wartość nie jest prawidłowy z typem ASCII.|
   |**Ctrl+Alt+Shift**|Użytkownik musi nacisnąć klawisz **Ctrl**, **Alt**, i **Shift** przed **klucz** wartość nie jest prawidłowy z typem ASCII.|

**Klucz** właściwość ustawia rzeczywistego klucza do użycia jako akcelerator.

Poniżej znajdują się wpisy prawne **klucz** właściwości w tabeli akceleratora:

   |Wartość|Opis|
   |-----------|-----------------|
   |Liczba całkowita między 0 a 255 w formacie dziesiętnym.|Wartość określa, czy wartość jest traktowana jako ASCII i ANSI w następujący sposób:<br/><br/>   -Cyfr są zawsze interpretowane jako odpowiadający mu klucz, a nie jako wartości ASCII lub ANSI.<br/>   -Wartości z zakresu od 1 do 26, gdy poprzedzony zerami, są interpretowane jako ^ od A do ^ Z, która reprezentuje wartość ASCII litery alfabetu, po naciśnięciu z **Ctrl** przytrzymanie klawisza.<br/>   -Wartościami z 27 32 są zawsze interpretowane jako wartości dziesiętne trzycyfrowy 027 za pośrednictwem 032.<br/>   -Wartości z kolekcji 033 do 255, czy poprzedzony przez użytkownika 0 nie będą interpretowane jako wartości ANSI.|
   |Znak pojedynczego klawiatury.|Wielkie litery A - Z lub cyfry 0 - 9 mogą być ASCII lub wirtualny wartości klucza. Jakikolwiek inny znak jest ASCII tylko.|
   |Klawiatury pojedynczy znak z zakresu A - Z (tylko wielkie litery), poprzedzony daszek (^), na przykład ^ C.|Ta opcja wprowadza wartość ASCII klucza po naciśnięciu klawisza z **Ctrl** przytrzymanie klawisza.|
   |Wszystkie prawidłowe wirtualny identyfikator klawisza.|Z listy rozwijanej **klucz** pola w tabeli akceleratora zawiera standardowe wirtualnych identyfikatorów klucza.|

> [!NOTE]
> Podczas wprowadzania wartości ASCII **modyfikator** opcje właściwości są ograniczone. Jest tylko klawisz control dostępne do użytku **Alt** klucza.

> [!TIP]
> Skrót do definiowania klawiszem skrótu prawym przyciskiem myszy wpis lub wiele wpisów w tabeli akceleratora, następnie wybierz **dalej wpisany klucz** i naciśnij klawisze lub kombinacji klawiszy na klawiaturze.
>
> To **dalej wpisany klucz** polecenia jest także dostępny z **Edytuj** menu.

**Typu** właściwość określa, czy klawisz skrótu skojarzony akcelerator **identyfikator** jest interpretowany jako wartość klucza ASCII/ANSI lub kombinacji klawisza wirtualnego (VIRTKEY).

- Jeśli **typu** właściwość **ASCII**, **modyfikator** właściwości mogą być tylko `None` lub `Alt`, lub może być akceleratora, który używa **Ctrl** klucza, określony przez poprzedzający klucza o `^`.

- Jeśli **typu** właściwość **VIRTKEY**, dowolnej kombinacji **modyfikator** i **klucz** wartości jest prawidłowy.

> [!NOTE]
> Jeśli chcesz wprowadzić wartość w tabeli akceleratora i wartości traktowane jako ASCII/ANSI, wybierz **typu** dla wpisu w tabeli i wybierz pozycję **ASCII** z listy rozwijanej. Jednak jeśli używasz **dalej wpisany klucz** polecenia **Edytuj** menu, aby określić **klucz**, należy zmienić **typu** właściwość **VIRTKEY** do **ASCII** *przed* wprowadzania **klucz** kodu.

## <a name="accelerator-tables"></a>Tabel akceleratora

W projekcie w języku C++ możesz edytować bezpośrednio za pomocą edycji w miejscu, w tabeli akceleratora **Edytor klawiszy skrótów**.

Poniższe procedury dotyczą używanie stron właściwości standardowych, jednak zarówno edycji w miejscu, jak i metody strony właściwości mają ten sam wynik. Zmiany wprowadzone za pomocą stron właściwości lub edycji w miejscu są natychmiast odzwierciedlane w tabeli klawiszy skrótu.

### <a name="to-edit-in-an-accelerator-table"></a>Edytowanie w tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz wpis w tabeli, a następnie wybierz, aby aktywować edycji w miejscu.

1. W polu kombi z listy rozwijanej wybierz lub wpisz w miejscu, aby wprowadzić zmiany:

   - Aby uzyskać **identyfikator**, wybierz z listy lub wpisz, aby edytować.

   - Aby uzyskać **modyfikator**, wybierz z listy.

   - Aby uzyskać **klucz**, wybierz z listy lub wpisz, aby edytować.

   - Aby uzyskać **typu**, wybierz opcję **ASCII** lub **VIRTKEY** z listy.

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Aby znaleźć wpisu w tabeli akceleratora Otwórz

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz główny kolumny, aby posortować alfabetycznie zawartości kolumny. Na przykład wybierz **identyfikator** do wyświetlenia wszystkich identyfikatorów w tabeli akceleratora alfabetycznie.

   Można następnie przejrzyj listę i znajdź pozycję.

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Aby dodać wpis do tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Kliknij prawym przyciskiem myszy w tabeli klawiszy skrótów, a następnie wybierz **nowy akcelerator**, lub zaznacz pusty wiersz w dolnej części tabeli.

1. Wybierz **identyfikator** z listy rozwijanej w **identyfikator** pole lub wpisz nowy *identyfikator* w **identyfikator** pole.

1. Typ *klucz* ma być używany jako akcelerator, lub kliknij prawym przyciskiem myszy i wybierz pozycję **dalej wpisany klucz** kombinację klawiszy lub przejdź do menu **Edytuj**  >  **Następny wciśnięty klawisz**.

1. Zmiana **modyfikator** i **typu**, jeśli to konieczne i naciśnij klawisz **Enter**.

> [!NOTE]
> Upewnij się, że wszystkie akceleratorów, jaką zdefiniujesz są unikatowe. Może mieć kilka kombinacji klawiszy przypisane do tego samego Identyfikatora przy użyciu efektu wpływu, na przykład **Ctrl**+**P** i **F8** zarówno można przypisać do ID_PRINT. Jednak masz kombinację klawiszy przypisane do więcej niż jeden identyfikator nie będzie działać poprawnie, na przykład **Ctrl**+**Z** przypisane do ID_SPELL_CHECK i ID_THESAURUS.

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>Aby usunąć wpis z tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz wpis, aby usunąć lub naciśnij i przytrzymaj **Ctrl** lub **Shift** klucza podczas zaznaczania, aby wybrać wiele wpisów.

1. Kliknij prawym przyciskiem myszy i wybierz polecenie **Usuń**, lub przejdź do menu **Edytuj** > **Usuń**.

> [!TIP]
> Można również nacisnąć klawisz **Usuń** klawisz, aby usunąć.

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Przenoszenie lub kopiowanie wpisu tabeli akceleratora do innego pliku skryptu zasobów

1. Otwórz tabel akceleratora w obu plików skryptu zasobu, a następnie wybierz wpis, który chcesz przenieść.

1. Z **Edytuj** menu, wybierz **kopiowania** lub **Wytnij**.

1. Wybierz wpis w pliku skryptu zasobu docelowego, a także z **Edytuj** menu, wybierz **Wklej**.

> [!NOTE]
> Możesz również klawisze skrótów, kopiowania i wklejania.

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Aby zmienić właściwości kilku klawiszy skrótów

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz klawisze skrótów chcesz zmienić, przytrzymując **Ctrl** klucza, zgodnie z wybraniu każdej z nich.

1. Przejdź do [okno właściwości](/visualstudio/ide/reference/properties-window) i wpisz wartości, które mają wszystkich wybranych akceleratorów, aby udostępnić.

> [!NOTE]
> Każda wartość modyfikator jest wyświetlana jako właściwość typu Boolean w **właściwości** okna. Jeśli zmienisz [modyfikator](../windows/accelerator-modifier-property.md) wartość w **właściwości** oknie tabeli akceleratora traktuje nowy modyfikator jako dodatek do wszelkich modyfikatorów, które były wcześniej dostępne. W związku z tym Jeśli ustawisz wartości modyfikatora musisz ustawić dla wszystkich z nich, aby upewnić się, że każdy akcelerator udostępnia takie same **modyfikator** ustawienia.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Klawisze skrótów](../windows/predefined-accelerator-keys.md)<br/>