---
title: Zalecane tagi dla komentarzy do dokumentacji (komentarze do dokumentacji języka C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 1648d0eb019a3aad25641d7f6a7edd1ba26acf7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336171"
---
# <a name="recommended-tags-for-documentation-comments"></a>Zalecane tagi przeznaczone do komentarzy dokumentacji

Kompilator MSVC będzie przetwarzać komentarze dokumentacji w kodzie i tworzy plik xdc dla każdego compiland, a xdcmake.exe przetworzy pliki .xdc do pliku xml. Przetwarzanie pliku xml w celu utworzenia dokumentacji jest szczegółem, który należy zaimplementować w lokacji.

Tagi są przetwarzane na konstrukcjach, takich jak typy i elementy członkowskie typu.

Tagi muszą natychmiast poprzedzać typy lub elementy członkowskie.

> [!NOTE]
> Komentarze dokumentacji nie mogą być stosowane do obszaru nazw lub definicji poza wierszem dla właściwości i zdarzeń; uwagi do dokumentacji muszą zawierać deklaracje w klasie.

Kompilator przetworzy dowolny znacznik, który jest prawidłowy XML. Następujące tagi zapewniają powszechnie używane funkcje w dokumentacji użytkownika:

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<>kodu](code-visual-cpp.md)|[\<przykład>](example-visual-cpp.md)|
|wyjątek>1 [ \< ](exception-visual-cpp.md)|obejmują>1 [ \< ](include-visual-cpp.md)|[\<>listy](list-visual-cpp.md)|
|[\<>para](para-visual-cpp.md)|param>1 [ \< ](param-visual-cpp.md)|paramref>1 [ \< ](paramref-visual-cpp.md)|
|pozwolenie>1 [ \< ](permission-visual-cpp.md)|[\<uwagi>](remarks-visual-cpp.md)|[\<zwraca>](returns-visual-cpp.md)|
|patrz>1 [ \< ](see-visual-cpp.md)|również>1 [ \< ](seealso-visual-cpp.md)|[\<podsumowanie>](summary-visual-cpp.md)|
|[\<wartość>](value-visual-cpp.md)|||

1. Kompilator weryfikuje składnię.

W bieżącej wersji kompilator MSVC `<paramref>`nie obsługuje tagu obsługiwanego przez inne kompilatory programu Visual Studio. Visual C++ `<paramref>` może obsługiwać w przyszłej wersji.

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](xml-documentation-visual-cpp.md)
