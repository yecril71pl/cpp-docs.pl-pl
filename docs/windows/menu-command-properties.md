---
title: Polecenia menu (C++)
ms.date: 02/15/2019
helpviewer_keywords:
- menu items, properties
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
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
ms.openlocfilehash: c9abf46907c473d4cf6d9e945038f70aa75bfc48
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026282"
---
# <a name="menu-commands-c"></a>Polecenia menu (C++)

Poniższe informacje są organizowane według **Menu** właściwości, które pojawiają się w [okno właściwości](/visualstudio/ide/reference/properties-window) po wybraniu polecenia menu. Te są wymieniane alfabetycznie mimo że **właściwości** okno umożliwia również wyświetlanie tych właściwości według kategorii.

|Właściwość|Opis|
|--------------|-----------------|
|**BREAK**|Może być jedną z następujących wartości:<br/>  - **Brak**: Bez przerwy. Domyślnie włączone.<br/>  - **Kolumna**: Statyczne menu ta wartość umieszcza polecenie menu w nowym wierszu.<br/>      Ta wartość wyskakujących menu umieszcza polecenia menu w nową kolumnę z nie jednoznaczny kolumn.<br/>      Ustawienie tej właściwości ma wpływ na wygląd menu tylko w czasie wykonywania, nie Edytor menu.<br />   - **Pasek**: Taki sam jak **kolumny** z wyjątkiem sytuacji, menu podręczne tę wartość oddziela nowej kolumny od starego kolumnę z pionowym wierszem.<br/>      Ustawienie tej właściwości określa wygląd menu tylko w czasie wykonywania, nie w **Edytor Menu**.|
|**Podpis**|Tekst etykiety polecenia menu (Nazwa menu). Aby utworzyć kolekcję liter w podpisie menu poleceń klawisz dostępu, należy poprzedzić handlowe "i" (&).|
|**Zaznaczone**|Jeśli **True**, polecenia menu jest domyślnie zaznaczone. Wpisz: **wartość logiczna**. Wartość domyślna: **FALSE**.|
|**Włączone**|Jeśli **False**, element menu jest wyłączona.|
|**Wyszarzony**|Jeśli **True**, polecenia menu jest początkowo wygaszone i nieaktywnych. Wpisz: **wartość logiczna**. Wartość domyślna: **FALSE**.|
|**Pomoc**|Wyrównuje elementu menu z prawej strony. Wartość domyślna: **FALSE**.<br/><br/>Na przykład **pomocy** polecenia menu jest zawsze po prawej stronie we wszystkich aplikacjach Windows. Jeśli ustawisz tę właściwość, element menu, ten element pojawi się po bardzo prawej stronie i na końcu menu. Dotyczy to elementów najwyższego poziomu.|
|**Identyfikator**|Symbol zdefiniowany w pliku nagłówkowym. Wpisz: **Symbol**, **całkowitą**, lub **ciąg w cudzysłowach**.<br/><br/>Może używać dowolny symbol, który jest powszechnie dostępne we wszystkich edytory, nawet jeśli [okno właściwości](/visualstudio/ide/reference/properties-window) nie zawiera listy rozwijanej, wybierz z.|
|**Popup**|Jeśli **True**, polecenia menu jest menu podręczne. Wpisz: **wartość logiczna**. Wartość domyślna: **Wartość true,** najwyższego poziomu menu na pasku menu, w przeciwnym razie **False**.|
|**wiersz**|Zawiera tekst wyświetlany na pasku stanu wyróżnionego to polecenie menu. Tekst jest umieszczany w tabeli ciągów zawierających ten sam identyfikator jak polecenie menu.<br/><br/>Ta właściwość jest dostępna dla wszystkich typów projektów, ale funkcje środowiska wykonawczego jest określone MFC.|
|**Wyjustuj do prawej do lewej**|Po prawej stronie uzasadnia polecenia menu na pasku menu w czasie wykonywania. Wpisz: **wartość logiczna**. Wartość domyślna: **FALSE**.|
|**Od prawej do lewej kolejności**|Umożliwia polecenia menu wyświetlić od prawej do lewej, gdy interfejs jest zlokalizowane dla dowolnego języka, który odczytuje prawej do lewej, takich jak hebrajskiego i arabskiego.|
|**Separator**|Jeśli **True**, polecenia menu jest separatorem. Wpisz: **wartość logiczna**. Wartość domyślna: **FALSE**.|

## <a name="associate-menu-commands"></a>Kojarzenie poleceń Menu

Są często razy polecenia menu a kombinacja klawiszy, Wydaj to samo polecenie program. Polecenia identyczne są wydawane za pomocą **Edytor Menu** można przypisać tego samego identyfikatora zasobu, do polecenia menu i wpis w tabeli klawiszy skrótu aplikacji. Następnie Edytuj [podpis](../windows/menu-command-properties.md) polecenia menu, aby wyświetlić nazwę klawisza skrótu.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Aby skojarzyć polecenia menu z klawiszem skrótu

1. W **Edytor Menu**, wybierz polecenia menu, które ma.

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), Dodaj nazwę klawisza skrótu do **podpis** właściwości:

   - Następujący podpis menu Typ sekwencji ucieczki dla karty (\t) tak, aby wszystkie klawisze skrótów menu są pozostawiane wyrównane.

   - Wpisz nazwę klawisz modyfikujący (**Ctrl**, **Alt**, lub **Shift**) ze znakiem plus (**+**) i nazwę, litery, lub symbol dodatkowy klucz.

   Na przykład, aby przypisać **Ctrl**+**O** do **Otwórz** polecenie **pliku** menu modyfikowanie polecenia menu  **Podpis** tak, aby wyglądało następujący tekst:

   ```
   &Open...\tCtrl+O
   ```

   Polecenia menu w **Edytor Menu** zostanie zaktualizowany w celu odzwierciedlenia nowy podpis w trakcie pisania.

1. [Tworzenie wpisu tabeli akceleratora](../windows/adding-an-entry-to-an-accelerator-table.md) w **akceleratora** edytora i przypisać ją w taki sam identyfikator jak polecenie menu. Użyj kombinacji klawiszy, które uważasz, że będzie łatwa do zapamiętania.

Aplikacja MFC można wyświetlić tekst opisu dla każdego polecenia menu, które użytkownik może wybrać. Wyświetlić tekst opisu, przypisując ciąg tekstowy do każdego menu polecenie przy użyciu **monitu** właściwość **właściwości** okna. Jeśli w ciągu [tabeli ciągów](../windows/string-editor.md) których identyfikator jest taki sam jak polecenia, aplikacji MFC będą automatycznie wyświetlać ten zasób ciąg w pasku stanu w uruchomionej aplikacji po użytkownik myszy nad element menu.

- Aby skojarzyć polecenia menu z stanu paska ciąg tekstowy w aplikacjach MFC w **Edytor Menu**, wybierz polecenie menu. W [okno właściwości](/visualstudio/ide/reference/properties-window), wpisz tekst skojarzony z nim stan paska w **monitu** pole.

W projekcie w języku C++ klawisza dostępu (Mnemonik, który umożliwia użytkownikowi wybranie w menu za pomocą klawiatury) można przypisać do menu i poleceń menu.

- Aby przypisać klawisza dostępu (skrót), polecenia menu, wpisz znak (`&`) przed litery w nazwie menu lub nazwa polecenia, aby określić tę literę jako odpowiedniego klucza dostępu. 

   Na przykład "& plik" ustawia **Alt**+**F** jako klawisza skrótu dla **pliku** menu w aplikacji napisanych dla Microsoft Windows.

   Element menu będzie udostępniać widoczne oznaką jedna z liter ma do niej przypisany klawisz skrótu. Następujące list, zostaną wyświetlone handlowe "i" podkreślone (warunkowe w systemie operacyjnym).

> [!NOTE]
> Upewnij się, wszystkie klucze dostępu w menu są unikatowe, klikając prawym przyciskiem myszy menu i wybierając pozycję **Sprawdź mnemonik**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytor menu](../windows/menu-editor.md)<br/>

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->