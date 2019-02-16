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
ms.openlocfilehash: 90ef142336cf88c5e40f78f6cc651b2bb35a0f6c
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320643"
---
# <a name="accelerator-editor-c"></a>Edytor klawiszy skrótów (C++)

Tabeli klawiszy skrótu jest zasób Windows C++, który zawiera listę klawisze skrótów (znany także jako klawisze skrótów) i identyfikatory poleceń, które są skojarzone z nimi. Program może mieć więcej niż jednej tabeli akceleratora.

Zwykle akceleratorów są używane jako skróty klawiaturowe dla poleceń programu, które są również dostępne w menu lub paska narzędzi. Jednak można użyć tabeli akceleratora do definiowania kombinacji klawiszy dla polecenia, które nie mają skojarzonych z nimi obiektu interfejsu użytkownika.

Możesz użyć [Widok klas](/visualstudio/ide/viewing-the-structure-of-code) można dołączyć klucza polecenia klawiszy skrótów do kodu.

Aby uzyskać listę predefiniowanych klawiszy skrótów, zobacz [wstępnie zdefiniowane klawisze skrótów](../windows/predefined-accelerator-keys.md).

   > [!TIP]
   > Podczas korzystania z **akceleratora** edytora, możesz kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów z najczęściej używanymi poleceniami. Dostępne polecenia zależą od tego, wskaźnik wskazuje na.

   > [!NOTE]
   > Windows nie pozwalają na tworzenie tabel akceleratora puste. Jeśli utworzenia tabeli akceleratora żadnych wpisów, zostanie usunięta automatycznie po zapisaniu tabeli.

## <a name="accelerator-properties"></a>Właściwości klawiszy skrótów

Można ustawić właściwości klawiszy skrótów w [okno właściwości](/visualstudio/ide/reference/properties-window) w dowolnym momencie. Można również użyć **akceleratora** edytora, aby zmodyfikować właściwości klawiszy skrótów w tabeli klawiszy skrótu. Zmiany wprowadzone przy użyciu **właściwości** okna lub **akceleratora** Edytor ma ten sam wynik: zmiany są natychmiast odzwierciedlane w tabeli klawiszy skrótu.

### <a name="id-property"></a>ID — Właściwość

**Identyfikator** właściwości odwołuje się do każdego wpisu tabeli akceleratora w kodzie programu. Ten wpis jest wartość polecenia, który program otrzyma po naciśnięciu klawisza skrótu lub kombinację klawiszy. Aby akceleratora taki sam jak element menu, należy ich identyfikatorów takie same (tak długo, jak identyfikator tabeli klawiszy skrótu jest taki sam jak identyfikator zasobu menu).

Istnieją trzy właściwości dla każdego identyfikator akceleratora: **modyfikator** właściwości **klucz** właściwości i **typu** właściwości.

#### <a name="modifier-property"></a>Modifier — Właściwość

**Modyfikator** właściwość ustawia kontroli kombinacje klawiszy dla akceleratora.

> [!NOTE]
> W **właściwości** okna, właściwość ta pojawia się jako trzy osobne **logiczna** właściwości, które mogą być kontrolowane niezależnie: **ALT**, **Ctrl**, i **Shift**.

Poniżej znajdują się wpisy prawne **modyfikator** właściwości w tabeli akceleratora:

   |Wartość|Opis|
   |-----------|-----------------|
   |**Brak**|Użytkownik naciśnie tylko **klucz** wartość. Ta wartość jest najbardziej efektywne używana przy użyciu wartości ASCII/ANSI 001 za pośrednictwem 026, który jest interpretowany jako ^ od A do ^ Z (**Ctrl + A** za pośrednictwem **Ctrl + Z**).|
   |**ALT**|Użytkownik musi nacisnąć klawisz **Alt** klucza przed **klucz** wartość.|
   |**Ctrl**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
   |**SHIFT**|Użytkownik musi nacisnąć klawisz **Shift** klucza przed **klucz** wartość.|
   |**Ctrl+Alt**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza i **Alt** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
   |**Ctrl+Shift**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza i **Shift** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
   |**Alt+Shift**|Użytkownik musi nacisnąć klawisz **Alt** klucza i **Shift** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
   |**Ctrl+Alt+Shift**|Użytkownik musi nacisnąć klawisz **Ctrl**, **Alt**, i **Shift** przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|

#### <a name="key-property"></a>Key — Właściwość

**Klucz** właściwość ustawia rzeczywistego klucza do użycia jako akcelerator.

Poniżej znajdują się wpisy prawne **klucz** właściwości w tabeli akceleratora:

   |Wartość|Opis|
   |-----------|-----------------|
   |Liczba całkowita między 0 a 255 w formacie dziesiętnym.|Wartość określa, czy wartość jest traktowana jako ASCII i ANSI w następujący sposób:<br/><br/>-Cyfr są zawsze interpretowane jako odpowiadający mu klucz, a nie jako wartości ASCII lub ANSI.<br/>-Wartości z zakresu od 1 do 26, gdy poprzedzony zerami, są interpretowane jako ^ od A do ^ Z, która reprezentuje wartość ASCII litery alfabetu, po naciśnięciu z **Ctrl** przytrzymanie klawisza.<br/>-Wartościami z 27 32 są zawsze interpretowane jako wartości dziesiętne trzycyfrowy 027 za pośrednictwem 032.<br/>-Wartości z kolekcji 033 do 255, czy poprzedzony przez użytkownika 0 nie będą interpretowane jako wartości ANSI.|
   |Znak pojedynczego klawiatury.|Wielkie litery A - Z lub cyfry 0 - 9 mogą być ASCII lub wirtualny wartości klucza. jakikolwiek inny znak jest ASCII tylko.|
   |Klawiatury pojedynczy znak z zakresu A - Z (tylko wielkie litery), poprzedzony daszek (^) (na przykład ^ C).|Ta opcja wprowadza wartość ASCII klucza po naciśnięciu klawisza z **Ctrl** przytrzymanie klawisza.|
   |Wszystkie prawidłowe wirtualny identyfikator klawisza.|Pole listy rozwijanej klucza w tabeli akceleratora zawiera standardowe wirtualnych identyfikatorów klucza.|

> [!NOTE]
> Podczas wprowadzania wartości ASCII, opcje właściwości modyfikator są ograniczone. Jest tylko klawisz control dostępne do użytku **Alt** klucza.

> [!TIP]
> Innym sposobem zdefiniowania klawiszem skrótu jest kliknij prawym przyciskiem myszy wpis lub wiele wpisów w tabeli akceleratora, wybierz polecenie **dalej wpisany klucz** z menu skrótów, a następnie naciśnij klawisze lub kombinacji klawiszy na klawiaturze. **Dalej wpisany klucz** polecenia jest także dostępny z **Edytuj** menu.

#### <a name="type-property"></a>Type — Właściwość

**Typu** właściwość określa, czy klawisz skrótu skojarzony identyfikator akceleratora, jest interpretowany jako wartość klucza ASCII/ANSI lub kombinacji klawisza wirtualnego (VIRTKEY).

- Jeśli **typu** właściwość jest ASCII, **modyfikator** właściwości mogą być tylko `None` lub `Alt`, lub może być akceleratora, który używa **Ctrl** klucza () określony przez poprzedzający klucza o `^`).

- Jeśli **typu** właściwość jest VIRTKEY i dowolną kombinację `Modifier` i `Key` wartości jest prawidłowy.

> [!NOTE]
> Jeśli chcesz wprowadzić wartość w tabeli akceleratora i wartości traktowane jak ASCII/ANSI, po prostu kliknij **typu** wpisu w tabeli i ASCII wybierz z listy rozwijanej. Jednak jeśli używasz **dalej wpisany klucz** polecenia (**Edytuj** menu) do określenia `Key`, należy zmienić **typu** właściwość VIRTKEY ASCII *przed* wprowadzania `Key` kodu.

## <a name="accelerator-tables"></a>Tabel akceleratora

W projekcie w języku C++ możesz edytować bezpośrednio za pomocą edycji w miejscu, w tabeli akceleratora **akceleratora** edytora.

Poniższe procedury dotyczą używanie stron właściwości standardowych, jednak zarówno edycji w miejscu, jak i metody strony właściwości mają ten sam wynik. Zmiany wprowadzone za pomocą stron właściwości lub edycji w miejscu są natychmiast odzwierciedlane w tabeli klawiszy skrótu.

### <a name="to-edit-in-an-accelerator-table"></a>Edytowanie w tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

1. Wybierz wpis w tabeli, a następnie wybierz, aby aktywować edycji w miejscu.

1. Wybierz z listy rozwijanej kombi lub wpisz w miejscu, aby wprowadzić zmiany.

   - Aby uzyskać **identyfikator**, wybierz z listy lub wpisz, aby edytować.

   - Aby uzyskać **modyfikator**, wybierz z listy.

   - Aby uzyskać **klucz**, wybierz z listy lub wpisz, aby edytować.

   - Aby uzyskać **typu**, wybierz opcję **ASCII** lub **VIRTKEY** z listy.

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Aby znaleźć wpisu w tabeli akceleratora Otwórz

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

1. Wybierz główny kolumny, aby posortować alfabetycznie zawartości kolumny. Na przykład wybierz **identyfikator** do wyświetlenia wszystkich identyfikatorów w tabeli akceleratora alfabetycznie.

Można następnie przejrzyj listę i znajdź pozycję.

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Aby dodać wpis do tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

1. Kliknij prawym przyciskiem myszy w tabeli klawiszy skrótów, a następnie wybierz **nowy akcelerator** z menu skrótów, lub wybierz wpis pusty wiersz na końcu tabeli.

1. Wybierz **identyfikator** z listy rozwijanej w identyfikatorze pole lub wpisz nowy identyfikator w **identyfikator** pole.

1. Typ **klucz** chcesz użyć jako akcelerator lub kliknij prawym przyciskiem myszy i wybrać **dalej wpisany klucz** z menu skrótów, aby ustawić kombinację klawiszy ( **dalej wpisany klucz** polecenia również dostępne z **Edytuj** menu).

1. Zmiana **modyfikator** i **typu**, jeśli to konieczne.

1. Naciśnij klawisz **wprowadź**.

   > [!NOTE]
   > Upewnij się, że wszystkie akceleratorów, jaką zdefiniujesz są unikatowe. Może mieć kilka kombinacji klawiszy przypisane do tego samego Identyfikatora przy użyciu efektu wpływu, na przykład **Ctrl** + **P** i **F8** zarówno można przypisać do ID_PRINT. Jednak masz kombinację klawiszy przypisane do więcej niż jeden identyfikator nie będzie działać poprawnie, na przykład **Ctrl** + **Z** przypisane do ID_SPELL_CHECK i ID_THESAURUS.

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>Aby usunąć wpis z tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

1. Wybierz wpis, który chcesz usunąć. (Naciśnij i przytrzymaj **Ctrl** lub **Shift** klucza podczas zaznaczania, aby wybrać wiele wpisów.)

1. Kliknij prawym przyciskiem myszy i wybierz polecenie **Usuń** z menu skrótów (lub wybierz **Usuń** z **Edytuj** menu).

> [!TIP]
> Skrót do usunięcia jest naciśnięcie **Usuń** klucza.

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Przenoszenie lub kopiowanie wpisu tabeli akceleratora do innego pliku skryptu zasobów

1. Otwórz tabel akceleratora w obu plików skryptu zasobu.

1. Wybierz wpis, który chcesz przenieść.

1. Z **Edytuj** menu, wybierz **kopiowania** lub **Wytnij**.

1. Wybierz wpis w pliku skryptu zasobu docelowego.

1. Z **Edytuj** menu, wybierz **Wklej**.

   > [!NOTE]
   > Możesz również klawisze skrótów, kopiowania i wklejania.

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Aby zmienić właściwości kilku klawiszy skrótów

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

1. Wybierz klawisze skrótów chcesz zmienić, przytrzymując **Ctrl** klucza, zgodnie z wybraniu każdej z nich.

1. Przejdź do [okno właściwości](/visualstudio/ide/reference/properties-window) i wpisz wartości, które mają wszystkich wybranych akceleratorów, aby udostępnić.

   > [!NOTE]
   > Każda wartość modyfikator jest wyświetlana jako właściwość typu Boolean w **właściwości** okna. Jeśli zmienisz [modyfikator](../windows/accelerator-modifier-property.md) wartość w **właściwości** oknie tabeli akceleratora traktuje nowy modyfikator jako dodatek do wszelkich modyfikatorów, które były wcześniej dostępne. W związku z tym Jeśli ustawisz wartości modyfikatora będzie należy ustawić wszystkie z nich, aby upewnić się, że każdy akcelerator udostępnia takie same **modyfikator** ustawienia.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Wstępnie zdefiniowane klawisze skrótów](../windows/predefined-accelerator-keys.md)<br/>