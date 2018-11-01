---
title: Obsługa formatu Unicode
ms.date: 1/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: fea49bff2a4563b8617e19636e27afbae1c55811
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501689"
---
# <a name="support-for-unicode"></a>Obsługa formatu Unicode

Unicode jest specyfikacji do obsługi wszystkich zestawów znaków, łącznie z tymi, które nie mogą być reprezentowane w tylko jednego bajtu (oznacza to, że większość z nich). Jeśli programujesz na rynku międzynarodowym, zalecane jest użycie obu Unicode lub [zestaw znaków wielobajtowych](../text/support-for-multibyte-character-sets-mbcss.md) znaków (MBCS) lub kodu programu, można je tworzyć w obu, zmieniając z przełącznikiem.

Znak dwubajtowy jest kod znaku wielojęzyczny 2-bajtowych. Dziesiątki tysięcy znaków, zawierających prawie wszystkie znaki używane w nowoczesnych przetwarzania danych na całym świecie, w tym techniczne symboli i publikowania znaków specjalnych, może być reprezentowany zgodnie ze specyfikacją Unicode jako pojedynczy wide znaków zakodowanych przy przy użyciu UTF-16. Znaki, które nie mogą być przedstawione na tylko jeden znak dwubajtowy, może być reprezentowany w parze Unicode przy użyciu funkcji para zastępcza Unicode. Ponieważ prawie każdy znak w typowym zastosowaniem jest reprezentowany w UTF-16 w jednym 16-bitowych znaków dwubajtowych, przy użyciu znaków dwubajtowych upraszcza programowania, korzystając z zestawów znaków międzynarodowych. Znaki dwubajtowe kodowane w formacie UTF-16LE (w przypadku little-endian) są macierzystym znaków formatu Windows.

Ciąg znaków dwubajtowych jest reprezentowany jako `wchar_t[]` macierz, a następnie jest wskazywany przez `wchar_t*` wskaźnika. Dowolnego znaku ASCII może być reprezentowany jako znak dwubajtowy przez dodanie przedrostka litera L do znaku. Na przykład L '\0' jest kończącego znaku NULL całej (16-bitowe). Podobnie dowolny ciąg ASCII literału może być reprezentowany jako literał ciągu znaków dwubajtowych, przez dodanie przedrostka litera L na literał ASCII (L "Witaj,").

Ogólnie rzecz biorąc znaki dwubajtowe zajmują więcej miejsca w pamięci niż znaki wielobajtowe, ale są szybsze do procesu. Ponadto tylko jeden ustawienia regionalne mogą być reprezentowane w czasie wielobajtowego kodowania, natomiast zestawy wszystkich znaków na świecie są jednocześnie reprezentowane przez reprezentację Unicode.

Struktura MFC jest obsługujące format Unicode w całym, a w ramach MFC Unicode, umożliwiając przy użyciu makr przenośne, jak pokazano w poniższej tabeli.

## <a name="portable-data-types-in-mfc"></a>Przenośne typy danych w MFC

|Typ danych inne niż przenośna|Zastępuje to makro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (Win32 dane typu) `LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Win32 dane typu) `LPCWSTR`|`LPCTSTR`|

Klasa `CString` używa `_TCHAR` jako jego podstawowy i udostępnia operatory i konstruktory konwersji łatwe. Większość operacji na ciągach obsługi standardu Unicode mogą być napisane przy użyciu tej samej logiki, używane do obsługi zestawu znaków Windows ANSI, z tą różnicą, że podstawowa jednostka operacji jest znak 16-bitowych, zamiast bajt 8-bitowych. W przeciwieństwie do pracy z zestawów znaków wielobajtowych, nie muszą (i nie powinien) traktować znak Unicode, tak, jakby był to dwa odrębne bajty. Jednak masz do czynienia z możliwością jednego znaku, reprezentowane przez para zastępcza szerokich znaków. Ogólnie rzecz biorąc nie napisać kod, który przyjęto założenie, że długość ciągu jest taka sama jak liczba znaków, czy wąskiego lub szerokiego, czy zawiera on.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Użyj MFC Unicode i znaków wielobajtowych pomocy technicznej z zestawem (znaków MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Włącz Unicode w programach](../text/international-enabling.md)

- [Włącz w programach Unicode i MBCS](../text/internationalization-strategies.md)

- [Unicode można użyć do utworzenia programu międzynarodowych](../text/unicode-programming-summary.md)

- [Informacje o zaletach Unicode](../text/benefits-of-character-set-portability.md)

- [Użyj wmain, więc do mojego programu można przekazać argumenty znaków dwubajtowych](../text/support-for-using-wmain.md)

- [Wyświetlane jest podsumowanie programowania Unicode](../text/unicode-programming-summary.md)

- [Więcej informacji na temat mapowania typ ogólny tekst przenośności bajt zerowej szerokości](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Zobacz także

[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)<br/>
[Obsługa używania funkcji wmain](../text/support-for-using-wmain.md)