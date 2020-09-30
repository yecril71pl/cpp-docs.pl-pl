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
ms.openlocfilehash: a950e7d0156d1b952782fddcdff26718fcf0e291
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504325"
---
# <a name="menu-commands-c"></a>Polecenia menu (C++)

Poniższe informacje są zorganizowane zgodnie z właściwościami **menu** , które pojawiają się w [oknie właściwości](/visualstudio/ide/reference/properties-window) po wybraniu polecenia menu. Są one wyświetlane alfabetycznie, mimo że okno **Właściwości** umożliwia również wyświetlanie tych właściwości według kategorii.

|Właściwość|Opis|
|--------------|-----------------|
|**Przerwij**|Może być jedną z następujących wartości:<br/>  - **Brak**: brak przerwy. Jest to opcja domyślna.<br/>  - **Kolumna**: dla statycznych menu, ta wartość umieszcza polecenie menu w nowym wierszu.<br/>      W przypadku menu podręcznych ta wartość umieszcza polecenie menu w nowej kolumnie bez linii podziału między kolumnami.<br/>      Ustawienie tej właściwości wpływa na wygląd menu tylko w czasie wykonywania, a nie w edytorze menu.<br />   - **Pasek**: taki sam jak **kolumna** z wyjątkiem, dla menu podręcznych, ta wartość oddziela nową kolumnę od starej kolumny z linią pionową.<br/>      Ustawienie tej właściwości wpływa na wygląd menu tylko w czasie wykonywania, a nie w **Edytorze menu**.|
|**Caption**|Tekst, który jest oznakowany poleceniem menu (nazwa menu). Aby wykonać jedną z liter w podpisie polecenia menu, klawisz skrótu, poprzedź go znakiem handlowego "i" (&).|
|**Zaznaczono**|W przypadku opcji **true**polecenie menu jest początkowo zaznaczone. Typ: **bool**. Wartość domyślna: **false**.|
|**Włączone**|W przypadku **wartości false**element menu jest wyłączony.|
|**Wygaszone**|W przypadku **wartości true**polecenie menu jest początkowo wyszarzone i nieaktywne. Typ: **bool**. Wartość domyślna: **false**.|
|**Pomoc**|Wyrównuje element menu w prawo. Wartość domyślna: **false**.<br/><br/>Na przykład polecenie menu **Pomoc** jest zawsze z prawej strony we wszystkich aplikacjach systemu Windows. Jeśli ustawisz tę właściwość w elemencie menu, ten element pojawi się po prawej stronie i na końcu menu. Dotyczy elementów najwyższego poziomu.|
|**ID**|Symbol zdefiniowany w pliku nagłówkowym. Type: **symbol**, **Liczba całkowita**lub **ciąg ujęty w cudzysłów**.<br/><br/>Możesz użyć dowolnego symbolu, który jest powszechnie dostępny w którymkolwiek z edytorów, nawet jeśli [okno właściwości](/visualstudio/ide/reference/properties-window) nie zawiera listy rozwijanej, z której można wybrać opcję.|
|**Okno podręczne**|W przypadku **wartości true**polecenie menu jest menu podręcznym. Typ: **bool**. Wartość domyślna: **true** dla menu najwyższego poziomu na pasku menu, w przeciwnym razie **false**.|
|**Monit**|Zawiera tekst, który ma być wyświetlany na pasku stanu, gdy to polecenie menu jest wyróżnione. Tekst zostanie umieszczony w tabeli ciągów z tym samym identyfikatorem co polecenie menu.<br/><br/>Ta właściwość jest dostępna dla dowolnego typu projektu, ale funkcjonalność czasu wykonywania jest specyficzna dla MFC.|
|**Wyjustuj od prawej do lewej**|Right — Justuje polecenie menu na pasku menu w czasie wykonywania. Typ: **bool**. Wartość domyślna: **false**.|
|**Kolejnooć od prawej do lewej**|Zezwala na wyświetlanie poleceń menu po lewej stronie, gdy interfejs jest zlokalizowany w dowolnym języku, który odczytuje od prawej do lewej, na przykład hebrajski lub arabski.|
|**Separator**|W przypadku **wartości true**polecenie menu jest separatorem. Typ: **bool**. Wartość domyślna: **false**.|

## <a name="associate-menu-commands"></a>Kojarzenie poleceń menu

Często zdarza się, aby polecenie menu i kombinację klawiatury były wystawiane przez to samo polecenie programu. Identyczne polecenia są wydawane przy użyciu **edytora menu** do przypisania tego samego identyfikatora zasobu do polecenia menu i do wpisu w tabeli akceleratora aplikacji. Następnie można edytować [podpis](../windows/menu-command-properties.md) polecenia menu, aby wyświetlić nazwę klawisza skrótu.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Aby skojarzyć polecenie menu z klawiszem skrótu

1. W **Edytorze menu**wybierz odpowiednie polecenie menu.

1. W [oknie właściwości](/visualstudio/ide/reference/properties-window)Dodaj nazwę klawisza skrótu do właściwości **Caption** :

   - Po podpisie menu wpisz sekwencję ucieczki dla karty (\t), tak aby wszystkie klawisze skrótów menu były wyrównane do lewej.

   - Wpisz nazwę klawisza modyfikującego (**Ctrl**, **Alt**lub **SHIFT**), a następnie znak plus ( **+** ) oraz nazwę, literę lub symbol dodatkowego klucza.

   Na przykład, aby przypisać **klawisz Ctrl** + **o** do polecenia **Otwórz** w menu **plik** , należy zmodyfikować **podpis** polecenia menu, tak aby wyglądał wyglądać następująco:

   ```
   &Open...\tCtrl+O
   ```

   Polecenie menu w **Edytorze menu** jest aktualizowane w celu odzwierciedlenia nowego podpisu podczas jego wpisywania.

1. [Utwórz wpis akceleratora w tabeli](./accelerator-editor.md) w edytorze **akceleratora** i przypisz go do tego samego identyfikatora co polecenie menu. Skorzystaj z kombinacji klawiszy, którą myślisz.

Aplikacja MFC może wyświetlać tekst opisowy dla każdego polecenia menu, które użytkownik może wybrać. Wyświetlanie tekstu opisowego przez przypisanie ciągu tekstowego do każdego polecenia menu przy użyciu właściwości **monitu** w oknie **Właściwości** . Jeśli w [tabeli ciągów](../windows/string-editor.md) znajduje się ciąg, którego identyfikator jest taki sam jak polecenie, aplikacja MFC automatycznie wyświetli ten zasób ciągu na pasku stanu uruchomionej aplikacji, gdy użytkownik umieści wskaźnik myszy nad elementem menu.

- Aby skojarzyć polecenie menu z ciągiem tekstowym paska stanu w aplikacjach MFC, w **Edytorze menu**wybierz polecenie menu. W [oknie właściwości](/visualstudio/ide/reference/properties-window)wpisz skojarzony tekst paska stanu w polu **monit** .

W projekcie języka C++ można przypisać klucz dostępu (element, który umożliwia użytkownikowi wybranie menu za pomocą klawiatury) do menu i poleceń menu.

- Aby przypisać klucz dostępu (skrót) do polecenia menu, wpisz znak handlowego "i" ( `&` ) przed literą w nazwie menu lub nazwie polecenia, aby określić tę literę jako odpowiedni klucz dostępu.

   Na przykład "&plik" ustawia **Alt** + **F** jako klawisz skrótu menu **plik** w aplikacjach utworzonych dla systemu Microsoft Windows.

   Element menu zapewni widoczną kontrolkę, do której jeden z liter ma przypisany klawisz skrótu. Litera po znaku "handlowe" będzie wyświetlana jako podkreślona (w zależności od systemu operacyjnego).

> [!NOTE]
> Upewnij się, że wszystkie klucze dostępu w menu są unikatowe, klikając prawym przyciskiem myszy menu i wybierając pozycję **zaznacz**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor menu](../windows/menu-editor.md)

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->
