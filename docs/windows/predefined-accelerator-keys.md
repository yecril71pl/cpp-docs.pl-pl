---
title: Klawisze skrótów (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: bb407538f254df5f187ff91b85a8eaa753a52287
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027522"
---
# <a name="accelerator-keys-c"></a>Klawisze skrótów (C++)

## <a name="predefined-accelerator-keys"></a>Wstępnie zdefiniowane klawisze skrótów

Istnieje kilka wstępnie zdefiniowane klawisze skrótów, które mogą być częścią projektu aplikacji Windows. Niektóre z tych wirtualnych kluczy są w środowisku Windows. Inne osoby obsługuje przeglądarki lub aplikacji nieobsługujących kodu Unicode. W dowolnym akceleratora, można użyć dowolnego z tych kluczy.

|Key|Opis|
|---------|-----------------|
|VK_ACCEPT|(Editor IME) Zaakceptuj|
|VK_BROWSER_BACK|(Windows) Przeglądarka **ponownie** klucza|
|VK_BROWSER_FAVORITES|(Windows) Przeglądarka **ulubione** klucza|
|VK_BROWSER_FORWARD|(Windows) Przeglądarka **do przodu** klucza|
|VK_BROWSER_HOME|(Windows) Przeglądarka **Start** i **Home** klucza|
|VK_BROWSER_REFRESH|(Windows) Przeglądarka **Odśwież** klucza|
|VK_BROWSER_SEARCH|(Windows) Przeglądarka **wyszukiwania** klucza|
|VK_BROWSER_STOP|(Windows) Przeglądarka **zatrzymać** klucza|
|VK_CONVERT|Konwertuj (Editor IME)|
|VK_FINAL|Tryb końca (Editor IME)|
|VK_HANGUEL|EDITOR (IME) Tryb Hanguel (utrzymywana ze względu na zgodność, użyj VK_HANGUL)|
|VK_HANGUL|EDITOR (IME) Tryb Hangul|
|VK_HANJA|EDITOR (IME) Tryb Hanja|
|VK_JUNJA|EDITOR (IME) Tryb Junja|
|VK_KANA|EDITOR (IME) Tryb Kana|
|VK_KANJI|EDITOR (IME) Tryb Kanji|
|VK_LAUNCH_APP1|(Windows) **Start aplikacja 1** klucza|
|VK_LAUNCH_APP2|(Windows) **Start 2 aplikacji** klucza|
|VK_LAUNCH_MAIL|(Windows) **Uruchamianie poczty** klucza|
|VK_LAUNCH_MEDIA_SELECT|(Windows) **Wybierz Media** klucza|
|VK_LCONTROL|**Po lewej stronie Ctrl** klucza|
|VK_LMENU|**Menu po lewej stronie** klucza|
|VK_LSHIFT|**Przesunięcia w lewo** klucza|
|VK_MEDIA_NEXT_TRACK|(Windows) **Następnej ścieżki** klucza|
|VK_MEDIA_PLAY_PAUSE|(Windows) **Media odtwarzany/wstrzymywany** klucza|
|VK_MEDIA_PREV_TRACK|(Windows) **Poprzedniej ścieżki** klucza|
|VK_MEDIA_STOP|(Windows) **Zatrzymać Media** klucza|
|VK_MODECHANGE|Żądanie zmiany trybu (IME)|
|VK_NONCONVERT|Nonconvert (Editor IME)|
|VK_OEM_1|(Windows) Dla Stanów Zjednoczonych, standardowy interfejs użytkownika **;:** klucza|
|VK_OEM_102|(Windows) Nawias kątowy klucz lub klucz ukośnik odwrotny na klawiaturze 102-key RT|
|VK_OEM_2|(Windows) Dla Stanów Zjednoczonych, standardowy interfejs użytkownika **/?** klawisz|
|VK_OEM_3|(Windows) Dla Stanów Zjednoczonych, standardowy interfejs użytkownika **`~** klucza|
|VK_OEM_4|(Windows) Dla Stanów Zjednoczonych, standardowy interfejs użytkownika **[{** klucza|
|VK_OEM_5|(Windows) Dla Stanów Zjednoczonych, standardowy interfejs użytkownika **\\ &#124;** klucza|
|VK_OEM_6|(Windows) Dla Stanów Zjednoczonych, standardowy interfejs użytkownika **]}** klucza|
|VK_OEM_7|(Windows) Dla Stanów Zjednoczonych standardowy interfejs użytkownika, klucz "pojedynczego — oferta/podwójny cudzysłów"|
|VK_OEM_COMMA|(Windows) Dla jakiegokolwiek kraju/regionu **,** klucza|
|VK_OEM_MINUS|(Windows) Dla jakiegokolwiek kraju/regionu **-** klucza|
|VK_OEM_PERIOD|(Windows) Dla jakiegokolwiek kraju/regionu **.** klawisz|
|VK_OEM_PLUS|(Windows) Dla jakiegokolwiek kraju/regionu **+** klucza|
|VK_PACKET|(Windows) Używany do przekazywania znaków Unicode, tak jakby one naciśnięć klawiszy.|
|VK_RCONTROL|**Po prawej stronie Ctrl** klucza|
|VK_RMENU|**Menu po prawej stronie** klucza|
|VK_RSHIFT|**Prawy Shift** klucza|
|VK_SLEEP|**Komputer uśpiony** klucza|
|VK_VOLUME_DOWN|(Windows) **Woluminu w dół** klucza|
|VK_VOLUME_MUTE|(Windows) **Woluminu Wycisz** klucza|
|VK_VOLUME_UP|(Windows) **Woluminu się** klucza|
|VK_XBUTTON1|(Windows) **X1** przycisk myszy|
|VK_XBUTTON2|(Windows) **X2** przycisk myszy|

## <a name="accelerator-key-association"></a>Skojarzenie klucza klawiszy skrótów

Wiele razy potrzebujesz element menu i kombinacja klawiszy, aby Wydaj to samo polecenie program. Wykonaj tę akcję, przypisując tego samego identyfikatora zasobu (identyfikator), element menu oraz wpis w tabeli akceleratora aplikacji. Następnie Edytuj podpis elementu menu, aby wyświetlić nazwę akceleratora. Aby uzyskać więcej informacji na temat elementów menu oraz klawiszy skrótów, zobacz [poleceń Menu](../windows/associating-a-menu-command-with-an-accelerator-key.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytor klawiszy skrótów](../windows/accelerator-editor.md)<br/>