---
title: Obsługa formatu Unicode
ms.date: 01/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: c30cb1fbfb1930b5e4b026e58c478f0099e8ecdf
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929923"
---
# <a name="support-for-unicode"></a>Obsługa formatu Unicode

Unicode to specyfikacja do obsługi wszystkich zestawów znaków, w tym tych, które nie mogą być reprezentowane w pojedynczym bajcie.  Jeśli planujesz Programowanie na rynku międzynarodowym, zalecamy użycie [zestawu znaków Unicode lub wielobajtowego](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS). Lub Zakoduj program, aby można było go skompilować przez zmianę przełącznika.

Znak dwubajtowy to kod 2-bitowy. Dziesiątki tysięcy znaków, składające się na prawie wszystkie znaki używane w nowoczesnej skali na całym świecie, w tym symbole techniczne i znaki specjalne publikacji, mogą być reprezentowane zgodnie ze specyfikacją Unicode jako pojedynczy znak dwubajtowy zakodowany przez przy użyciu UTF-16. Znaki, które nie mogą być reprezentowane w tylko jednym znaku dwubajtowym, mogą być reprezentowane w parze Unicode przy użyciu funkcji wieloskładnikowej pary Unicode. Ponieważ niemal każdy znak w typowym użyciu jest reprezentowany w UTF-16 w pojedynczym 16-bitowym znaku, za pomocą znaków dwubajtowych upraszcza programowanie z międzynarodowymi zestawami znaków. Znaki dwubajtowe zakodowane przy użyciu kodowania UTF-16LE (dla little-endian) są natywnym formatem znaków dla systemu Windows.

Ciąg znaków dwubajtowych jest reprezentowany jako `wchar_t[]` tablica i jest wskazywany `wchar_t*` przez wskaźnik. Dowolny znak ASCII może być reprezentowany jako znak dwubajtowy, tworząc prefiks litery L do znaku. Na przykład L ' \ 0 ' jest znakiem o ZEROWEj szerokości (16-bitowym). Podobnie każdy literał ciągu ASCII może być reprezentowany jako literał ciągu znaków dwubajtowych, tworząc prefiks litery L do literału ASCII (L "Hello").

Ogólnie rzecz biorąc, szerokie znaki pobierają więcej miejsca w pamięci niż znaki wielobajtowe, ale szybciej są przetwarzane. Ponadto w przypadku kodowania wielobajtowego można reprezentować tylko jedne ustawienia regionalne, natomiast wszystkie zestawy znaków na świecie są reprezentowane jednocześnie przez reprezentację Unicode.

Platforma MFC jest włączona w systemie Unicode, a MFC umożliwia włączenie standardu Unicode przy użyciu makr przenośnych, jak pokazano w poniższej tabeli.

## <a name="portable-data-types-in-mfc"></a>Przenośne typy danych w MFC

|Nieprzenośny typ danych|Zastąpione przez to makro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (Typ danych Win32),`LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Typ danych Win32),`LPCWSTR`|`LPCTSTR`|

Klasa `CString` używa`_TCHAR` jako bazy i zawiera konstruktory i operatory do łatwego konwersji. Większość operacji na ciągach dla Unicode można napisać przy użyciu tej samej logiki, która jest używana do obsługi zestawu znaków ANSI systemu Windows, z tą różnicą, że podstawowa jednostka operacji jest 16-bitowym znakiem, a nie 8-bitowym bajtem. W przeciwieństwie do pracy z zestawami znaków wielobajtowych nie ma potrzeby traktowania znaków Unicode, tak jakby były dwa odrębne bajty. Należy jednak koniecznie zaradzić sobie z możliwością pojedynczego znaku reprezentowanego przez wieloskładnikową parę znaków. Ogólnie rzecz biorąc nie należy pisać kodu, który zakłada, że długość ciągu jest taka sama jak liczba znaków w wąskim lub szerokim, która zawiera.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Korzystanie z obsługi zestawów znaków Unicode i wielobajtowych (MBCS) MFC](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Włącz Unicode w moim programie](../text/international-enabling.md)

- [Włącz zarówno kod Unicode, jak i MBCS w moim programie](../text/internationalization-strategies.md)

- [Używanie Unicode do tworzenia międzynarodowego programu](../text/unicode-programming-summary.md)

- [Poznaj zalety standardu Unicode](../text/benefits-of-character-set-portability.md)

- [Użyj wmain, aby można było przekazywać argumenty szerokich znaków do mojego programu](../text/support-for-using-wmain.md)

- [Zobacz Podsumowanie programowania Unicode](../text/unicode-programming-summary.md)

- [Dowiedz się więcej o mapowaniu tekstu ogólnego dla przenośności szerokości bajtów](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Zobacz także

[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)<br/>
[Obsługa używania funkcji wmain](../text/support-for-using-wmain.md)