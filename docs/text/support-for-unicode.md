---
title: "Obsługa formatu Unicode | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 1/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fde7674d30d84385eb1f94f42056a82bfaac99fe
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="support-for-unicode"></a>Obsługa formatu Unicode

Unicode jest specyfikacją do obsługi wszystkich zestawów znaków, łącznie z tymi, które nie mogą być reprezentowane w tylko jednego bajtu (to znaczy, większość z nich). Jeśli programowanie międzynarodowe rynku zalecane jest użycie obu Unicode lub [zestaw znaków wielobajtowych](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS) lub kodu programu, można je tworzyć bądź zmiana przełącznika.

Znaków dwubajtowych jest kodem 2-bajtowych wartości znakowych wielu języków. Dziesiątki tysięcy znaków, zawierających prawie wszystkie znaki używane w nowoczesnych przetwarzania danych na całym świecie, tym techniczne symboli i znaków specjalnych publikowania, może być reprezentowany według specyfikacji Unicode jako pojedynczy całej znak kodowane przez przy użyciu UTF-16. Znaki, których nie można przedstawić w jednego znaku dwubajtowe ma być reprezentowane w parę Unicode za pomocą funkcji para zastępcza Unicode. Ponieważ prawie każdego znaku najczęściej używanych jest reprezentowana w UTF-16 w jednym 16-bitowych znaków dwubajtowych, przy użyciu znaki dwubajtowe upraszcza programowanie z użyciem zestawu znaków międzynarodowych. Znaki dwubajtowe kodowane w formacie UTF-16LE (dla little endian) są formatu macierzystego znaków dla systemu Windows.

Ciąg znaków dwubajtowych jest reprezentowany jako `wchar_t[]` tablicy i jest wskazywana przez `wchar_t*` wskaźnika. Dowolny znak ASCII może być reprezentowana jako znaków dwubajtowych, prefiksu litera na znak. Na przykład L '\0' to przerywanie dwubajtowe (16-bitowy) **NULL** znaków. Podobnie dowolny ciąg ASCII literał może być reprezentowana jako literału ciągu znaków dwubajtowych, dodając litera na literał ASCII (L "Hello").

Ogólnie rzecz biorąc znaki dwubajtowe zająć więcej miejsca w pamięci, niż znaków wielobajtowych, ale są szybsze do procesu. Ponadto tylko jeden ustawień regionalnych może być reprezentowany w czasie przy użyciu kodowania wielobajtowe, natomiast zestawy wszystkich znaków w świecie są jednocześnie reprezentowane przez reprezentacja Unicode.

Struktura MFC jest obsługą Unicode w całym i wykonuje MFC Unicode włączenie przy użyciu makra przenośne, jak pokazano w poniższej tabeli.

## <a name="portable-data-types-in-mfc"></a>Przenośne typy danych w MFC

|Typ danych inne niż przenośna|Zastępuje to makro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (Win32 typu danych)`LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Win32 typu danych)`LPCWSTR`|`LPCTSTR`|

Klasa `CString` używa `_TCHAR` podstawowym i zapewnia łatwe konwersje konstruktory i operatory. Większość operacje na ciągach standardu Unicode można pisać przy użyciu tej samej logiki, używany do obsługi zestawu znaków ANSI systemu Windows z wyjątkiem tego, że podstawowa jednostka operacji jest znakiem 16-bitową zamiast bajtów 8-bitową. W przeciwieństwie do pracy z zestawów znaków wielobajtowych, nie trzeba (i nie powinien) Traktuj znaków Unicode, tak jakby był on dwa różne bajty. Jednak masz radzenia sobie z możliwości pojedynczy znak reprezentowany przez para zastępcza znaki dwubajtowe. Ogólnie rzecz biorąc nie pisania kodu, który przyjęto założenie, że długość ciągu jest taka sama jak liczba znaków, czy wąskie lub szerokie, że zawiera on.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Użyj MFC Unicode i znaków wielobajtowych obsługi zestawu (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Włącz Unicode w programach](../text/international-enabling.md)

- [Włącz zarówno Unicode i MBCS w programach](../text/internationalization-strategies.md)

- [Używaj Unicode do utworzenia programu międzynarodowych](../text/unicode-programming-summary.md)

- [Poznaj korzyści ze znaków Unicode](../text/benefits-of-character-set-portability.md)

- [Użyj wmain, do programu można przekazać argumenty znaków dwubajtowych](../text/support-for-using-wmain.md)

- [Widoczne jest podsumowanie programowania Unicode](../text/unicode-programming-summary.md)

- [Więcej informacji na temat mapowania zwykłego tekstu przenośności szerokość bajtów](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Zobacz także

[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)  
[Obsługa używania funkcji wmain](../text/support-for-using-wmain.md)  
