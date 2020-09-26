---
title: Edytor akceleratorów (C++)
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
ms.openlocfilehash: c98ff1fd44b73b3f204e9b952836c387f7f21146
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353093"
---
# <a name="accelerator-editor-c"></a>Edytor akceleratorów (C++)

Tabela akceleratorów to zasób systemu Windows w języku C++, który zawiera listę klawiszy skrótów, nazywanych skrótami klawiaturowymi oraz identyfikatory poleceń, które są z nimi skojarzone. Program może mieć więcej niż jedną tabelę akceleratorów.

Zwykle akceleratory są używane jako skróty klawiaturowe poleceń programu, które są również dostępne w menu lub pasku narzędzi. Można jednak użyć tabeli akceleratora do definiowania kombinacji klawiszy dla poleceń, do których nie jest skojarzony obiekt użytkownika-interfejs.

> [!TIP]
> Korzystając z **edytora akceleratorów**, kliknij prawym przyciskiem myszy, aby wyświetlić menu skrótów często używanych poleceń. Dostępne polecenia zależą od elementów wskazywanych przez wskaźnik.

Za pomocą [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code) można podpiąć polecenia klawiszy skrótów do kodu. Aby zapoznać się z listą wstępnie zdefiniowanych klawiszy skrótów, zobacz [klawisze skrótów](predefined-accelerator-keys.md).

> [!NOTE]
> System Windows nie pozwala na tworzenie pustych tabel akceleratorów. Jeśli utworzysz tabelę akceleratora bez wpisów, zostanie ona automatycznie usunięta podczas zapisywania tabeli.

## <a name="accelerator-properties"></a>Właściwości akceleratora

W dowolnym momencie możesz ustawić właściwości akceleratora w [okno właściwości](/visualstudio/ide/reference/properties-window) . Możesz również użyć **edytora akceleratorów** , aby zmodyfikować właściwości akceleratora w tabeli akceleratora. Zmiany wprowadzone przy użyciu okna **Właściwości** lub **edytora akceleratorów** mają taki sam wynik, zmiany są natychmiast odzwierciedlane w tabeli akceleratorów.

Właściwość **ID** odwołuje się do każdego wpisu tabeli akceleratorów w kodzie programu. Ten wpis jest wartością polecenia, którą program otrzymuje, gdy użytkownik naciśnie klawisz skrótu lub kombinację klawiszy. Aby ustawić akcelerator w taki sam sposób, jak element menu, ustaw **Identyfikator** tak samo, o ile **Identyfikator** tabeli akceleratora jest taki sam jak **Identyfikator** zasobu menu.

Każdy **Identyfikator** akceleratora ma trzy właściwości: **modyfikator**, **klucz**i **Typ**

Właściwość **modyfikator** ustawia kombinacje klawiszy kontroli dla akceleratora.

> [!NOTE]
> W oknie **Właściwości** Właściwość **modyfikator** jest wyświetlana jako trzy osobne właściwości **logiczne** , które mogą być sterowane niezależnie: **Alt**, **Ctrl**i **SHIFT**.

Poniżej przedstawiono wpisy prawne dla właściwości **modyfikator** w tabeli akceleratora:

   |Wartość|Opis|
   |-----------|-----------------|
   |**Brak**|Użytkownik naciska tylko wartość **klucza** .<br/><br/>Ta wartość jest najbardziej efektywnie używana z wartościami ASCII/ANSI 001 i 026, które są interpretowane jako ^ A przez ^ Z (**Ctrl + A** przez **Ctrl + z**).|
   |**+**|Użytkownik musi nacisnąć klawisz **Alt** przed wartością **klucza** .|
   |**Przytrzymaj**|Użytkownik musi nacisnąć klawisz **Ctrl** przed wartością **klucza** , która nie jest prawidłowa z typem ASCII.|
   |**Przesunięcia**|Użytkownik musi nacisnąć klawisz **SHIFT** przed wartością **klucza** .|
   |**Ctrl + Alt**|Użytkownik musi nacisnąć **klawisze CTRL** i **Alt** przed wartością **klucza** , która nie jest prawidłowa z typem ASCII.|
   |**Ctrl + Shift**|Użytkownik musi nacisnąć **klawisze CTRL** i **SHIFT** przed wartością **klucza** , która nie jest prawidłowa z typem ASCII.|
   |**Alt + Shift**|Użytkownik musi nacisnąć klawisze **Alt** i **SHIFT** przed wartością **klucza** , która nie jest prawidłowa z typem ASCII.|
   |**Ctrl + Alt + Shift**|Użytkownik musi nacisnąć **klawisze CTRL**, **Alt**i **SHIFT** przed wartością **klucza** , która nie jest prawidłowa z typem ASCII.|

Właściwość **Key** ustawia rzeczywisty klucz, który ma być używany jako akcelerator.

Poniżej znajdują się wpisy prawne dla właściwości **Key** w tabeli akceleratora:

   |Wartość|Opis|
   |-----------|-----------------|
   |Liczba całkowita z zakresu od 0 do 255 w formacie dziesiętnym.|Wartość określa, czy wartość jest traktowana jako ASCII czy ANSI w następujący sposób:<br/><br/>   -Numery pojedynczej cyfry są zawsze interpretowane jako odpowiadające im klucze, a nie jako wartości ASCII lub ANSI.<br/>   -Wartości od 1 do 26, gdy poprzedzają zera, są interpretowane jako ^ A za pośrednictwem ^ Z, który reprezentuje wartość ASCII liter alfabetu po naciśnięciu klawisza **Ctrl** .<br/>   -Wartości z 27-32 są zawsze interpretowane jako trzy wartości dziesiętne 027 do 032.<br/>   -Wartości od 033 do 255, niezależnie od tego, czy poprzedzają 0, czy nie są interpretowane jako wartości ANSI.|
   |Pojedynczy znak klawiatury.|Wielkie litery A-Z lub liczby 0-9 mogą być wartościami klucza ASCII lub. Każdy inny znak jest tylko w formacie ASCII.|
   |Pojedynczy znak klawiatury w zakresie A-Z (wielkie litery), poprzedzony karetką (^), na przykład ^ C.|Ta opcja wprowadza wartość ASCII klucza po naciśnięciu klawisza **Ctrl** .|
   |Dowolny prawidłowy identyfikator klucza wirtualnego.|Pole **klucza** listy rozwijanej w tabeli akceleratora zawiera listę standardowych identyfikatorów kluczy wirtualnych.|

> [!NOTE]
> Podczas wprowadzania wartości ASCII opcje właściwości **modyfikatora** są ograniczone. Jedynym kluczem kontroli dostępnym do użycia jest klawisz **Alt** .

> [!TIP]
> Skrót służący do definiowania klawisza skrótu to kliknięcie prawym przyciskiem myszy wpisu lub wielu wpisów w tabeli akceleratora, a następnie wybranie polecenia **Następny typ** i naciśnięcie dowolnego klawisza lub kombinacji klawiszy na klawiaturze.
>
> To polecenie **następnego typu klucza** jest również dostępne w menu **Edycja** .

Właściwość **Type** określa, czy kombinacja klawiszy skrótu skojarzona z **identyfikatorem** akceleratora jest interpretowana jako wartość klucza ASCII/ANSI lub kombinacja klucza wirtualnego (standardowym VIRTKEY).

- Jeśli właściwość **Type** ma wartość **ASCII**, właściwość **modyfikująca** może być `None` lub lub `Alt` może mieć akcelerator, który używa klawisza **Ctrl** , jak określono powyżej klawisza z `^` .

- Jeśli właściwość **Type** ma wartość **standardowym VIRTKEY**, dowolna kombinacja **modyfikatora** i wartości **klucza** jest prawidłowa.

> [!NOTE]
> Jeśli chcesz wprowadzić wartość do tabeli akceleratorów i mieć wartość traktowaną jako ASCII/ANSI, wybierz **Typ** wpisu w tabeli i wybierz pozycję **ASCII** z listy rozwijanej. Jeśli jednak do określenia **klucza**używasz polecenia **Next Key type** z menu **Edytuj** , musisz zmienić właściwość **Type** z **standardowym VIRTKEY** na **ASCII** *przed* wprowadzeniem kodu **klucza** .

## <a name="accelerator-tables"></a>Tabele akceleratora

W projekcie języka C++ można edytować tabelę akceleratora bezpośrednio z edycją w miejscu w **Edytorze akceleratorów**.

Poniższe procedury odnoszą się do używania standardowych stron właściwości, jednak zarówno Edycja w miejscu, jak i Metoda strony właściwości mają ten sam wynik. Zmiany wprowadzone przy użyciu stron właściwości lub edycji w miejscu są natychmiast odzwierciedlane w tabeli akceleratorów.

### <a name="to-edit-in-an-accelerator-table"></a>Aby edytować w tabeli akceleratora

1. Otwórz tabelę akceleratora, klikając dwukrotnie jej ikonę w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz wpis w tabeli i wybierz, aby uaktywnić edycję w miejscu.

1. Wybierz z listy rozwijanej lub wpisz w miejscu, aby wprowadzić zmiany:

   - Dla opcji **Identyfikator**wybierz z listy lub typ do edycji.

   - Dla **modyfikatora**wybierz z listy.

   - Dla opcji **klucz**wybierz z listy lub wpisz, aby edytować.

   - Dla opcji **Typ**wybierz z listy pozycję **ASCII** lub **standardowym VIRTKEY** .

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Aby znaleźć wpis w otwartej tabeli akceleratorów

1. Otwórz tabelę akceleratora, klikając dwukrotnie jej ikonę w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz nagłówek kolumny, aby posortować zawartość kolumny alfabetycznie. Na przykład wybierz pozycję **Identyfikator** , aby wyświetlić wszystkie identyfikatory w tabeli akceleratora alfabetycznie.

   Następnie można przeskanować listę i znaleźć wpis.

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Aby dodać wpis do tabeli akceleratora

1. Otwórz tabelę akceleratora, klikając dwukrotnie jej ikonę w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Kliknij prawym przyciskiem myszy w tabeli akceleratora i wybierz pozycję **Nowy akcelerator**lub zaznacz pusty wiersz w dolnej części tabeli.

1. Wybierz **Identyfikator** z listy rozwijanej w polu **ID** lub wpisz nowy *Identyfikator* w polu **ID** .

1. Wpisz *klucz* , który ma być używany jako akcelerator, lub kliknij prawym przyciskiem myszy i wybierz polecenie **Następny wpisany klucz** , aby ustawić kombinację klawiszy, lub przejdź do menu **Edytuj**  >  **Następny typ klucza**.

1. W razie potrzeby zmień **modyfikator** i **Typ**, a następnie naciśnij klawisz **Enter**.

> [!NOTE]
> Upewnij się, że wszystkie zdefiniowane akceleratory są unikatowe. Do ID_PRINT można przypisać kilka klawiszy przypisanych do tego samego identyfikatora bez żadnego niewłaściwego efektu, na przykład **Ctrl** + **P** i **F8** . Jednak posiadanie kombinacji klawiszy przypisanej do więcej niż jednego identyfikatora nie będzie działało prawidłowo, na przykład **Ctrl** + **Z** przypisano do obu ID_SPELL_CHECK i ID_THESAURUS.

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>Aby usunąć wpis z tabeli akceleratora

1. Otwórz tabelę akceleratora, klikając dwukrotnie jej ikonę w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz wpis, który chcesz usunąć, lub przytrzymaj klawisz **Ctrl** lub **SHIFT** podczas zaznaczania, aby wybrać wiele wpisów.

1. Kliknij prawym przyciskiem myszy i wybierz polecenie **Usuń**lub przejdź do menu **Edycja**  >  **Usuń**.

> [!TIP]
> Możesz również nacisnąć klawisz **delete** , aby usunąć.

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Aby przenieść lub skopiować wpis tabeli akceleratora do innego pliku skryptu zasobu

1. Otwórz tabele akceleratora w obu plikach skryptów zasobów i wybierz wpis, który chcesz przenieść.

1. Z menu **Edycja** wybierz polecenie **Kopiuj** lub **Wytnij**.

1. Wybierz wpis w pliku skryptu zasobu docelowego i z menu **Edycja** wybierz polecenie **Wklej**.

> [!NOTE]
> Możesz również użyć klawiszy skrótów do kopiowania i wklejania.

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Aby zmienić właściwości wielu klawiszy skrótów

1. Otwórz tabelę akceleratora, klikając dwukrotnie jej ikonę w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Wybierz klawisze skrótów, które chcesz zmienić, przytrzymując wciśnięty klawisz **Ctrl** podczas zaznaczania każdego z nich.

1. Przejdź do [okno właściwości](/visualstudio/ide/reference/properties-window) i wpisz wartości, które mają być współużytkowane przez wszystkie wybrane akceleratory.

> [!NOTE]
> Każda wartość modyfikatora jest wyświetlana jako właściwość logiczna w oknie **Właściwości** . Jeśli zmienisz wartość modyfikatora w oknie **Właściwości** , tabela akceleratora traktuje nowy modyfikator jako dodatek do wszystkich modyfikatorów, które wcześniej znajdowały się w tym miejscu. W związku z tym, jeśli ustawisz dowolne wartości modyfikatorów, musisz ustawić wszystkie z nich, aby upewnić się, że każdy akcelerator ma te same ustawienia **modyfikatora** .

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](resource-editors.md)<br/>
[Klawisze skrótów](predefined-accelerator-keys.md)<br/>
