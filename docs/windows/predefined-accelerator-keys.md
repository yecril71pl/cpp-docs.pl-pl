---
title: Klawisze skrótów (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: 4f838caa8ca9e4a996fa4cb8018d663c6c7aecea
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504295"
---
# <a name="accelerator-keys-c"></a>Klawisze skrótów (C++)

## <a name="predefined-accelerator-keys"></a>Wstępnie zdefiniowane klawisze skrótów

Istnieje wiele wstępnie zdefiniowanych klawiszy skrótów, które mogą być częścią projektu aplikacji systemu Windows. Niektóre z tych kluczy wirtualnych są przeznaczone dla środowiska systemu Windows. Inne obsługują przeglądarki lub aplikacje w formacie Unicode. Możesz użyć dowolnego z tych kluczy w dowolnym akceleratorze.

|Klucz|Opis|
|---------|-----------------|
|VK_ACCEPT|(IME) Zaakceptuj|
|VK_BROWSER_BACK|Systemy Przeglądarka, klawisz **powrotu**|
|VK_BROWSER_FAVORITES|Systemy Przeglądarka, klucz **Ulubione**|
|VK_BROWSER_FORWARD|Systemy Przeglądarka, klucz **do przodu**|
|VK_BROWSER_HOME|Systemy Przeglądarka, **początek** i klucz **Home**|
|VK_BROWSER_REFRESH|Systemy Przeglądarka, **Odśwież** klucz|
|VK_BROWSER_SEARCH|Systemy Przeglądarka, klucz **wyszukiwania**|
|VK_BROWSER_STOP|Systemy Przeglądarka, klawisz **stop**|
|VK_CONVERT|(IME) — konwersja|
|VK_FINAL|(IME) tryb końcowy|
|VK_HANGUEL|Konwersje Tryb Hanguel (obsługiwany w celu zapewnienia zgodności, użyj VK_HANGUL)|
|VK_HANGUL|Konwersje Tryb Hangul|
|VK_HANJA|Konwersje Tryb Hanja|
|VK_JUNJA|Konwersje Tryb Junja|
|VK_KANA|Konwersje Tryb kana|
|VK_KANJI|Konwersje Tryb kanji|
|VK_LAUNCH_APP1|Systemy **Uruchom klucz aplikacji 1**|
|VK_LAUNCH_APP2|Systemy Klucz **uruchamiania aplikacji 2**|
|VK_LAUNCH_MAIL|Systemy **Uruchom klucz poczty**|
|VK_LAUNCH_MEDIA_SELECT|Systemy **Wybierz klucz nośnika**|
|VK_LCONTROL|**Lewy klawisz Ctrl**|
|VK_LMENU|Klawisz **menu po lewej stronie**|
|VK_LSHIFT|**Lewy klawisz Shift**|
|VK_MEDIA_NEXT_TRACK|Systemy **Następny klucz śledzenia**|
|VK_MEDIA_PLAY_PAUSE|Systemy **Odtwórz/Wstrzymaj klucz multimedialny**|
|VK_MEDIA_PREV_TRACK|Systemy **Poprzedni klucz śledzenia**|
|VK_MEDIA_STOP|Systemy **Zatrzymaj klucz nośnika**|
|VK_MODECHANGE|(IME) żądanie zmiany trybu|
|VK_NONCONVERT|(IME) nie Konwertuj|
|VK_OEM_1|Systemy Dla standardowej klawiatury AMERYKAŃSKIej, klucz **;:**|
|VK_OEM_102|Systemy Klawisza kąta lub klawisza ukośnika odwrotnego na klawiaturze RT 102-klawisz|
|VK_OEM_2|Systemy W przypadku standardowej klawiatury AMERYKAŃSKIej **/?** key|
|VK_OEM_3|Systemy Dla standardowej klawiatury AMERYKAŃSKIej, **`~** klucz|
|VK_OEM_4|Systemy W przypadku standardowej klawiatury AMERYKAŃSKIej **[{** Key|
|VK_OEM_5|Systemy Dla standardowej klawiatury AMERYKAŃSKIej, klucz ** \\&#124;**|
|VK_OEM_6|Systemy Dla standardowej klawiatury AMERYKAŃSKIej, klucz **]}**|
|VK_OEM_7|Systemy W przypadku standardowej klawiatury AMERYKAŃSKIej klucz "Single-Quote/Double-Quote"|
|VK_OEM_COMMA|Systemy Dla każdego kraju/regionu, klucz **,**|
|VK_OEM_MINUS|Systemy Dla każdego kraju/regionu **-** klucz|
|VK_OEM_PERIOD|Systemy Dla każdego kraju/regionu, **.** key|
|VK_OEM_PLUS|Systemy Dla każdego kraju/regionu **+** klucz|
|VK_PACKET|Systemy Używane do przekazywania znaków Unicode, tak jakby były to naciśnięcia klawiszy.|
|VK_RCONTROL|Klawisz **Ctrl w prawo**|
|VK_RMENU|**Prawy klawisz menu**|
|VK_RSHIFT|Klawisz **Shift w prawo**|
|VK_SLEEP|Klucz **uśpienia komputera**|
|VK_VOLUME_DOWN|Systemy Klucz **w dół woluminu**|
|VK_VOLUME_MUTE|Systemy Klucz **wyciszenia woluminu**|
|VK_VOLUME_UP|Systemy Klucz **zapasowy**|
|VK_XBUTTON1|Systemy **X1** — przycisk myszy|
|VK_XBUTTON2|Systemy **X2** przycisk myszy|

## <a name="accelerator-key-association"></a>Skojarzenie klawisza skrótu

Wiele razy potrzebny jest element menu i kombinacja klawiatury, aby wydać to samo polecenie programu. Czynność tę należy wykonać, przypisując ten sam identyfikator zasobu (ID) do elementu menu i do wpisu w tabeli akceleratora aplikacji. Następnie można edytować podpis elementu menu, aby wyświetlić nazwę akceleratora. Aby uzyskać więcej informacji na temat elementów menu i klawiszy skrótów, zobacz [polecenia menu](./menu-command-properties.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytor akceleratorów](../windows/accelerator-editor.md)<br/>
