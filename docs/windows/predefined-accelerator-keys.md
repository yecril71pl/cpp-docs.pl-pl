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
ms.openlocfilehash: 6ef8f84564d6fd1957452971cb1e88dc99aa27e9
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320513"
---
# <a name="accelerator-keys-c"></a>Klawisze skrótów (C++)

## <a name="predefined-accelerator-keys"></a>Wstępnie zdefiniowane klawisze skrótów

Istnieje kilka wstępnie zdefiniowane klawisze skrótów, które mogą być częścią projektu aplikacji Windows. Niektóre z tych wirtualnych kluczy są w środowisku Windows. Inne przeglądarki pomocy technicznej lub aplikacji nieobsługujących kodu Unicode. W dowolnym akceleratora, można użyć dowolnego z tych kluczy.

|Key|Opis|
|---------|-----------------|
|VK_ACCEPT|Zaakceptuj edytora IME|
|VK_BROWSER_BACK|W systemie Windows: Przeglądarka kopii klucza|
|VK_BROWSER_FAVORITES|W systemie Windows: Klucz Ulubione w przeglądarce|
|VK_BROWSER_FORWARD|W systemie Windows: Klucz do przodu w przeglądarce|
|VK_BROWSER_HOME|W systemie Windows: Klucz uruchamiania przeglądarki i w domu|
|VK_BROWSER_REFRESH|W systemie Windows: Klucz odświeżenie przeglądarki|
|VK_BROWSER_SEARCH|W systemie Windows: Klucz wyszukiwania przeglądarki|
|VK_BROWSER_STOP|W systemie Windows: Klucz Stop przeglądarki|
|VK_CONVERT|Konwertuj edytora IME|
|VK_FINAL|Końcowe tryb edytora IME|
|VK_HANGUEL|Tryb IME Hanguel (utrzymywana ze względu na zgodność; Użyj VK_HANGUL)|
|VK_HANGUL|Tryb IME Hangul|
|VK_HANJA|Tryb IME Hanja|
|VK_JUNJA|Tryb IME Junja|
|VK_KANA|Tryb IME Kana|
|VK_KANJI|Tryb IME Kanji|
|VK_LAUNCH_APP1|W systemie Windows: Aplikacja 1 klucza|
|VK_LAUNCH_APP2|W systemie Windows: Rozpocznij klucz aplikacji 2|
|VK_LAUNCH_MAIL|W systemie Windows: Rozpocznij klucz poczty|
|VK_LAUNCH_MEDIA_SELECT|W systemie Windows: Wybierz klucz nośnika|
|VK_LCONTROL|Klawisz CONTROL po lewej stronie|
|VK_LMENU|Klawisz MENU po lewej stronie|
|VK_LSHIFT|Klucz PRZESUNIĘCIA w lewo|
|VK_MEDIA_NEXT_TRACK|W systemie Windows: Śledź kluczowi|
|VK_MEDIA_PLAY_PAUSE|W systemie Windows: Klucz nośnika odtwarzany/wstrzymywany|
|VK_MEDIA_PREV_TRACK|W systemie Windows: Poprzedni klucz toru|
|VK_MEDIA_STOP|W systemie Windows: Zatrzymaj klucza nośnika|
|VK_MODECHANGE|Żądania zmiany na tryb edytora IME|
|VK_NONCONVERT|Nonconvert edytora IME|
|VK_OEM_1|W systemie Windows: Dla Stanów Zjednoczonych, standardowy interfejs użytkownika ';: "klucz|
|VK_OEM_102|W systemie Windows: Nawias kątowy klucz lub klucz ukośnik odwrotny na klawiaturze 102-key RT|
|VK_OEM_2|W systemie Windows: Dla Stanów Zjednoczonych, standardowy interfejs użytkownika '/'? klawisz|
|VK_OEM_3|W systemie Windows: Dla Stanów Zjednoczonych standardowy interfejs użytkownika "~" klucz|
|VK_OEM_4|W systemie Windows: Dla Stanów Zjednoczonych, standardowy interfejs użytkownika "[{" klucz|
|VK_OEM_5|W systemie Windows: Dla Stanów Zjednoczonych, standardowy interfejs użytkownika "\\&#124;" klucz|
|VK_OEM_6|W systemie Windows: Dla Stanów Zjednoczonych, standardowy interfejs użytkownika "]}" klucza|
|VK_OEM_7|W systemie Windows: Dla Stanów Zjednoczonych standardowy interfejs użytkownika, klucz "pojedynczego — oferta/podwójny cudzysłów"|
|VK_OEM_COMMA|W systemie Windows: Dla jakiegokolwiek kraju/regionu, klucza ''|
|VK_OEM_MINUS|W systemie Windows: Dla jakiegokolwiek kraju/regionu "-" klucz|
|VK_OEM_PERIOD|W systemie Windows: Dla jakiegokolwiek kraju/regionu "." klucz|
|VK_OEM_PLUS|W systemie Windows: Dla jakiegokolwiek kraju/regionu, klucza '+'|
|VK_PACKET|W systemie Windows: Używany do przekazywania znaków Unicode, tak, jakby były naciśnięć klawiszy.|
|VK_RCONTROL|Klawisz CONTROL po prawej stronie|
|VK_RMENU|Klawisz MENU po prawej stronie|
|VK_RSHIFT|Klucz PRZESUNIĘCIA w prawo|
|VK_SLEEP|Klucz stanu uśpienia komputera|
|VK_VOLUME_DOWN|W systemie Windows: Wolumin szczegółów klucza|
|VK_VOLUME_MUTE|W systemie Windows: Wycisz klucz woluminu|
|VK_VOLUME_UP|W systemie Windows: Wolumin Konfigurowanie klucza|
|VK_XBUTTON1|W systemie Windows: X1 myszy przycisk|
|VK_XBUTTON2|W systemie Windows: X2 myszy przycisk|

## <a name="accelerator-key-association"></a>Skojarzenie klucza klawiszy skrótów

Wiele razy potrzebujesz element menu i kombinacja klawiszy, aby Wydaj to samo polecenie program. Możesz to zrobić, przypisując tego samego identyfikatora zasobu (identyfikator), element menu oraz wpis w tabeli akceleratora aplikacji. Następnie Edytuj podpis elementu menu, aby wyświetlić nazwę akceleratora. Aby uzyskać więcej informacji na temat elementów menu oraz klawiszy skrótów, zobacz [Kojarzenie elementów Menu z klawiszem skrótu](../windows/associating-a-menu-command-with-an-accelerator-key.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor klawiszy skrótów](../windows/accelerator-editor.md)<br/>