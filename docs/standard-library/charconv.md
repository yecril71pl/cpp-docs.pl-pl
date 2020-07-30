---
title: '&lt;charconv&gt;'
ms.date: 07/22/2020
f1_keywords:
- <charconv>
helpviewer_keywords:
- charconv header
ms.openlocfilehash: 59807749105512e0eb61acfdf60ef463febbc3a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87246123"
---
# <a name="ltcharconvgt"></a>&lt;charconv&gt;

Szybko przekonwertuj sekwencję znaków na liczbę całkowitą lub zmiennoprzecinkową i inny sposób.
Jednym ze sposobów korzystania z tej biblioteki jest pisanie i roundtrip wartości zmiennoprzecinkowych w plikach JSON i tekstowych.

Funkcje konwersji są dostrajane pod kątem wydajności, a także obsługują najkrótsze zachowanie. Zachowanie funkcji najkrótszej rundy oznacza, że gdy liczba jest konwertowana na znaki, jest zapisywana tylko wystarczająca precyzja, aby umożliwić odzyskiwanie pierwotnej liczby podczas konwertowania tych znaków z powrotem na zmiennoprzecinkową. Żadna inna funkcja CRT lub STL nie udostępnia tej funkcji.

Oto niektóre zalety korzystania z `<charconv>` biblioteki:

- Sekwencja znaków reprezentująca wartość liczbową nie musi być zakończona wartością null. Podobnie, gdy liczba jest konwertowana na znaki, wynik nie jest zakończony znakiem null.
- Funkcje konwersji nie przydzielają pamięci. W każdym przypadku jesteś właocicielem buforu.
- Funkcje konwersji nie generują. Zwracają strukturę, która zawiera informacje o błędach.
- Konwersje nie są rozróżniane w trybie zaokrąglania środowiska uruchomieniowego.
- Konwersje nie są oparte na ustawieniach regionalnych. Zawsze drukują i analizują punkty dziesiętne jako "." nigdy nie jako "," dla ustawień regionalnych, które używają przecinków.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<charconv>

**Przestrzeń nazw:** std

wymagany jest/std: c++ 17 lub nowszy.

## <a name="members"></a>Elementy członkowskie

### <a name="types"></a>Typy

| Typ | Opis |
|-|:-|
| [chars_format](chars-format-class.md) | Określa typ formatowania, na przykład naukowy, szesnastkowy i tak dalej. |
| [from_chars_result](from-chars-result-structure.md) | Przechowuje wynik `from_chars` konwersji. |
| [to_chars_result](to-chars-result-structure.md) | Przechowuje wynik `to_chars` konwersji. |

### <a name="functions"></a>Funkcje

| Funkcja | Opis |
|-|:-|
| [from_chars](charconv-functions.md#from_chars) | Konwertuj znaki na liczbę całkowitą, zmiennoprzecinkową lub podwójną. |
| [to_chars](charconv-functions.md#to_chars)| Przekonwertuj liczbę całkowitą, zmiennoprzecinkową lub podwójną na chars. |

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](cpp-standard-library-header-files.md)

