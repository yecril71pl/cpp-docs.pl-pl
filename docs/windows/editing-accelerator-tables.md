---
title: Edytowanie tabel akceleratora (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
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
ms.assetid: 56e24efb-d06b-4ed9-8915-1f99f725e247
ms.openlocfilehash: dfa0c26132378bcbe8a7f5203351134d91746aa7
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232178"
---
# <a name="editing-accelerator-tables-c"></a>Edytowanie tabel akceleratora (C++)

W projekcie w języku C++ możesz edytować bezpośrednio za pomocą edycji w miejscu, w tabeli akceleratora **akceleratora** edytora.

Poniższe procedury dotyczą używanie stron właściwości standardowych, jednak zarówno edycji w miejscu, jak i metody strony właściwości mają ten sam wynik. Zmiany wprowadzone za pomocą stron właściwości lub edycji w miejscu są natychmiast odzwierciedlane w tabeli klawiszy skrótu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

## <a name="to-edit-in-an-accelerator-table"></a>Edytowanie w tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

1. Wybierz wpis w tabeli, a następnie wybierz, aby aktywować edycji w miejscu.

1. Wybierz z listy rozwijanej kombi lub wpisz w miejscu, aby wprowadzić zmiany.

   - Aby uzyskać [identyfikator](id-property.md), wybierz z listy lub wpisz, aby edytować.

   - Aby uzyskać [modyfikator](../windows/accelerator-modifier-property.md), wybierz z listy.

   - Aby uzyskać [klucz](../windows/accelerator-key-property.md), wybierz z listy lub wpisz, aby edytować.

   - Aby uzyskać [typu](../windows/accelerator-type-property.md), wybierz opcję **ASCII** lub **VIRTKEY** z listy.

## <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Aby znaleźć wpisu w tabeli akceleratora Otwórz

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

1. Wybierz główny kolumny, aby posortować alfabetycznie zawartości kolumny. Na przykład wybierz **identyfikator** do wyświetlenia wszystkich identyfikatorów w tabeli akceleratora alfabetycznie.

Można następnie przejrzyj listę i znajdź pozycję.

## <a name="to-add-an-entry-to-an-accelerator-table"></a>Aby dodać wpis do tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

1. Kliknij prawym przyciskiem myszy w tabeli klawiszy skrótów, a następnie wybierz **nowy akcelerator** z menu skrótów, lub wybierz wpis pusty wiersz na końcu tabeli.

1. Wybierz [identyfikator](id-property.md) z listy rozwijanej w identyfikatorze pole lub wpisz nowy identyfikator w **identyfikator** pole.

1. Typ [klucz](../windows/accelerator-key-property.md) chcesz użyć jako akcelerator lub kliknij prawym przyciskiem myszy i wybrać **dalej wpisany klucz** z menu skrótów, aby ustawić kombinację klawiszy ( **dalej wpisany klucz** polecenia również dostępne z **Edytuj** menu).

1. Zmiana [modyfikator](../windows/accelerator-modifier-property.md) i [typu](../windows/accelerator-type-property.md), jeśli to konieczne.

1. Naciśnij klawisz **wprowadź**.

   > [!NOTE]
   > Upewnij się, że wszystkie akceleratorów, jaką zdefiniujesz są unikatowe. Może mieć kilka kombinacji klawiszy przypisane do tego samego Identyfikatora przy użyciu efektu wpływu, na przykład **Ctrl** + **P** i **F8** zarówno można przypisać do ID_PRINT. Jednak masz kombinację klawiszy przypisane do więcej niż jeden identyfikator nie będzie działać poprawnie, na przykład **Ctrl** + **Z** przypisane do ID_SPELL_CHECK i ID_THESAURUS.

## <a name="to-delete-an-entry-from-an-accelerator-table"></a>Aby usunąć wpis z tabeli akceleratora

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

1. Wybierz wpis, który chcesz usunąć. (Naciśnij i przytrzymaj **Ctrl** lub **Shift** klucza podczas zaznaczania, aby wybrać wiele wpisów.)

1. Kliknij prawym przyciskiem myszy i wybierz polecenie **Usuń** z menu skrótów (lub wybierz **Usuń** z **Edytuj** menu).

\- lub —

- Naciśnij klawisz **Usuń** klucza.

## <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Przenoszenie lub kopiowanie wpisu tabeli akceleratora do innego pliku skryptu zasobów

1. Otwórz tabel akceleratora w obu plików skryptu zasobu.

1. Wybierz wpis, który chcesz przenieść.

1. Z **Edytuj** menu, wybierz **kopiowania** lub **Wytnij**.

1. Wybierz wpis w pliku skryptu zasobu docelowego.

1. Z **Edytuj** menu, wybierz **Wklej**.

   > [!NOTE]
   > Możesz również klawisze skrótów, kopiowania i wklejania.

## <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Aby zmienić właściwości kilku klawiszy skrótów

1. Otwórz tabeli akceleratora, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

1. Wybierz klawisze skrótów chcesz zmienić, przytrzymując **Ctrl** klucza, zgodnie z wybraniu każdej z nich.

1. Przejdź do [okno właściwości](/visualstudio/ide/reference/properties-window) i wpisz wartości, które mają wszystkich wybranych akceleratorów, aby udostępnić.

   > [!NOTE]
   > Każda wartość modyfikator jest wyświetlana jako właściwość typu Boolean w **właściwości** okna. Jeśli zmienisz [modyfikator](../windows/accelerator-modifier-property.md) wartość w **właściwości** oknie tabeli akceleratora traktuje nowy modyfikator jako dodatek do wszelkich modyfikatorów, które były wcześniej dostępne. W związku z tym Jeśli ustawisz wartości modyfikatora będzie należy ustawić wszystkie z nich, aby upewnić się, że każdy akcelerator udostępnia takie same **modyfikator** ustawienia.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor klawiszy skrótów](../windows/accelerator-editor.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)
