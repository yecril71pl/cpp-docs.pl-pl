---
title: Kojarzenie poleceń Menu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
- status bars [C++], associating menu items
- menus [C++], status bar text
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
ms.openlocfilehash: f72fe5de3ef29b9575ef1a3138d4d114d7470fee
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703041"
---
# <a name="associating-menu-commands-c"></a>Kojarzenie poleceń Menu (C++)

Są często razy polecenia menu a kombinacja klawiszy, Wydaj to samo polecenie program. Polecenia identyczne są wydawane za pomocą **Menu** edytora, aby przypisać ten sam identyfikator zasobu, do polecenia menu i wpis w tabeli klawiszy skrótu aplikacji. Następnie Edytuj [podpis](../windows/menu-command-properties.md) polecenia menu, aby wyświetlić nazwę klawisza skrótu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Aby skojarzyć polecenia menu z klawiszem skrótu

1. W **Menu** edytora, wybierz polecenia menu, które ma.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), Dodaj nazwę klawisza skrótu do **podpis** właściwości:

   - Następujący podpis menu Typ sekwencji ucieczki dla karty (\t) tak, aby wszystkie klawisze skrótów menu są pozostawiane wyrównane.

   - Wpisz nazwę klawisz modyfikujący (**Ctrl**, **Alt**, lub **Shift**) ze znakiem plus (**+**) i nazwę, litery, lub symbol dodatkowy klucz.

       Na przykład, aby przypisać **Ctrl**+**O** do **Otwórz** polecenie **pliku** menu modyfikowanie polecenia menu  **Podpis** tak, aby wyglądało następujący tekst:

        ```
        &Open...\tCtrl+O
        ```

       Polecenia menu w **Menu** edytora jest aktualizowana w celu odzwierciedlenia nowy podpis w trakcie pisania.

1. [Tworzenie wpisu tabeli akceleratora](../windows/adding-an-entry-to-an-accelerator-table.md) w **akceleratora** edytora i przypisać ją w taki sam identyfikator jak polecenie menu. Użyj kombinacji klawiszy, które uważasz, że będzie łatwa do zapamiętania.

## <a name="to-associate-a-menu-command-with-a-status-bar-text-string-in-mfc-applications"></a>Aby skojarzyć polecenia menu z stanu paska ciąg tekstowy w aplikacjach MFC

Aplikacja MFC można wyświetlić tekst opisu dla każdego polecenia menu, które użytkownik może wybrać. Wyświetlić tekst opisu, przypisując ciąg tekstowy do każdego menu polecenie przy użyciu **monitu** właściwość **właściwości** okna. Jeśli w ciągu [tabeli ciągów](../windows/string-editor.md) których identyfikator jest taki sam jak polecenia, aplikacji MFC będą automatycznie wyświetlać ten zasób ciąg w pasku stanu w uruchomionej aplikacji po użytkownik myszy nad element menu.

1. W **Menu** edytora, wybierz polecenie menu.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), wpisz tekst skojarzony z nim stan paska w **monitu** pole.

> [!NOTE]
> Ten zestaw kroków wymaga MFC.

## <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Aby przypisać klawisza dostępu (skrót) do polecenia menu

W projekcie w języku C++ klawisza dostępu (Mnemonik, który umożliwia użytkownikowi wybranie w menu za pomocą klawiatury) można przypisać do menu i poleceń menu.

Wpisz znak (`&`) przed litery w nazwie menu lub nazwa polecenia, aby określić tę literę jako odpowiedniego klucza dostępu. Na przykład "& plik" ustawia **Alt**+**F** jako klawisza skrótu dla **pliku** menu w aplikacji napisanych dla Microsoft Windows.

   Element menu będzie udostępniać widoczne oznaką jedna z liter ma do niej przypisany klawisz skrótu. Następujące list, zostaną wyświetlone handlowe "i" podkreślone (warunkowe w systemie operacyjnym).

   > [!NOTE]
   > Upewnij się, wszystkie klucze dostępu w menu są unikatowe, klikając prawym przyciskiem myszy menu i wybierając pozycję **Sprawdź mnemonik** z menu skrótów.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor menu](../windows/menu-editor.md)<br/>
[Dodawanie poleceń do menu](../windows/adding-commands-to-a-menu.md)<br/>
[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
