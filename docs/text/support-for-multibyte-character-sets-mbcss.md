---
title: Obsługa zestawów znaków wielobajtowych (zestawy MBCS)
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
ms.openlocfilehash: c21b5b1ff059f26558749e904894cb5d15572519
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410567"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>Obsługa zestawów znaków wielobajtowych (zestawy MBCS)

Zestawy znaków wielobajtowych (zestawy MBCS) są starsze sposobem potrzeba do obsługi zestawów znaków, takich jak japońskim i chińskim, który nie może być przedstawiony w jednobajtowych. Jeśli przeprowadzasz nowych wdrożeniach należy używać Unicode dla wszystkich ciągów tekstowych, z wyjątkiem systemu może być ciągi, które nie są widoczne dla użytkowników końcowych. MBCS jest technologią starszą i nie jest zalecane w przypadku nowych wdrożeń.

Najbardziej typowe wdrożenie MBCS jest zestawów znaków dwubajtowych (DBCSs). Visual C++, ogólnie rzecz biorąc i MFC, w szczególności, w pełni jest włączona dla znaków Dwubajtowych.

Aby uzyskać przykłady Zobacz plików kodu źródłowego MFC.

Używane na rynkach, na których języków użyć dużych zestawów platformy najlepszą alternatywą do formatu Unicode jest MBCS. Biblioteka MFC obsługuje MBCS przy użyciu typów internationalizable danych i funkcji środowiska wykonawczego języka C. W kodzie, należy wykonać takie same.

W obszarze MBCS kodowania znaków w 1 lub 2 bajtów. Znaki 2-bajtowych, pierwszy lub bajt wiodący sygnalizuje, że ten plik i następny bajt należy interpretować jako jeden znak. Pierwszy bajt pochodzi z zakresu kodów zarezerwowany do użytku jako wiodące bajty. Zakresu bajtów może być wiodące bajty zależy od strony kodowej w użyciu. Na przykład japoński kodowych 932 wykorzystuje zakresie 0x81 za pośrednictwem 0x9F jako wiodące bajty, ale strona kodowa koreańska 949 używa innego zakresu.

Należy wziąć pod uwagę następujące usługi MBCS programowania.

Znaków MBCS w środowisku znaków MBCS może znajdować się w ciągach znaków, takich jak nazwy plików i katalogów.

### <a name="editing-operations"></a>Operacji edycji

Operacje w aplikacjach MBCS edytowania powinny działać na znaków, nie w bajtach. Daszek nie podzielić znak, **Strzałka w prawo** klucza należy przenieść jeden znak w prawo i tak dalej. **Usuń** należy usunąć znaku; **Cofnij** powinien ponownie.

### <a name="string-handling"></a>Obsługa ciągu

W aplikacji, która używa MBCS Obsługa ciągu stwarza szczególne problemy. Mieszane z obu szerokości znaków w ciągu jednego; w związku z tym należy pamiętać, aby wyszukać wiodące bajty.

### <a name="run-time-library-support"></a>Obsługa biblioteki wykonawczej

Obsługa biblioteki wykonawczej C i MFC MBCS, Unicode i jednobajtowych programowania. Ciągi znaków jednobajtowych są przetwarzane przy użyciu `str` rodziny funkcji wykonawczej MBCS ciągi są przetwarzane z odpowiednimi `_mbs` funkcji i ciągi Unicode są przetwarzane z odpowiednimi `wcs` funkcji. Implementacji funkcji elementu członkowskiego klasy MFC używać przenośnego funkcje środowiska uruchomieniowego, które mapują okolicznościach prawo do normalnych `str` rodziny, funkcje MBCS lub funkcji Unicode, zgodnie z opisem w "Przenośność MBCS/Unicode."

### <a name="mbcsunicode-portability"></a>Przenośność MBCS/Unicode

Przy użyciu pliku nagłówka w pliku tchar.h, tworzyć MBCS, Unicode i jednobajtowych aplikacji z tego samego źródła. Tchar.h definiuje makra prefiksem *_tcs* , które mapowania na `str`, `_mbs`, lub `wcs` funkcje, zgodnie z potrzebami. Aby skompilować MBCS, zdefiniuj symbol `_MBCS`. Aby skompilować Unicode, zdefiniuj symbol `_UNICODE`. Domyślnie `_UNICODE` jest zdefiniowana dla aplikacji MFC. Aby uzyskać więcej informacji, zobacz [mapowania typ ogólny-tekst w pliku tchar.h](../text/generic-text-mappings-in-tchar-h.md).

> [!NOTE]
>  Zachowanie jest niezdefiniowane, jeśli zdefiniujesz zarówno `_UNICODE` i `_MBCS`.

Pliki nagłówkowe Mbctype.h i Mbstring.h definiują MBCS specyficzne funkcje i makra, które może być konieczne w niektórych przypadkach. Na przykład `_ismbblead` informujący o tym, czy określone bajtów w ciągu jest bajtem wiodącym.

For międzynarodowymi przenośność kodu program jest połączony z [Unicode](../text/support-for-unicode.md) lub znak wielobajtowy, który ustawia (zestawy MBCS).

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Włącz MBCS w programach](../text/international-enabling.md)

- [Włącz w programach Unicode i MBCS](../text/internationalization-strategies.md)

- [Używają MBCS do utworzenia programu międzynarodowych](../text/mbcs-programming-tips.md)

- [Wyświetlane jest podsumowanie programowania MBCS](../text/mbcs-programming-tips.md)

- [Więcej informacji na temat mapowania typ ogólny tekst przenośności bajt zerowej szerokości](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Zobacz także

[Tekst i ciągi](../text/text-and-strings-in-visual-cpp.md)<br/>
[Obsługa MBCS w programie Visual C++](../text/mbcs-support-in-visual-cpp.md)
