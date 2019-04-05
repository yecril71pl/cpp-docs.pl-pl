---
title: Tagi zalecane dla komentarzy do dokumentacji (komentarze dokumentacji C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 2a6a2c3983c10579a6cd96b69be81aa7df8b8ee7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027899"
---
# <a name="recommended-tags-for-documentation-comments"></a>Zalecane tagi przeznaczone do komentarzy dokumentacji

Kompilator MSVC będą przetwarzane komentarze dokumentacji w kodzie i tworzy plik .xdc dla każdego compiland — i xdcmake.exe będzie przetwarzać plików xdc do pliku XML. Przetwarzanie pliku XML w celu utworzenia dokumentacji jest szczegółów, który musi zostać wdrożone w lokacji.

Tagi są przetwarzane w konstrukcji, takich jak typy i elementy członkowskie typu.

Tagi musi bezpośrednio poprzedzać typów ani elementów członkowskich.

> [!NOTE]
>  Komentarze dokumentacji nie można zastosować do przestrzeni nazw lub na Brak definicji wiersza dla właściwości i zdarzeń; komentarze dokumentacji musi w deklaracjach w swojej klasie.

Kompilator przetworzy dowolnymi tagami, które jest prawidłowym kodem XML. Następujące znaczniki zawierają powszechnie używanych funkcji w dokumentacji użytkownika:

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<code>](code-visual-cpp.md)|[\<przykład >](example-visual-cpp.md)|
|[\<wyjątek >](exception-visual-cpp.md)1|[\<obejmują >](include-visual-cpp.md)1|[\<list>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|[\<param>](param-visual-cpp.md)1|[\<paramref>](paramref-visual-cpp.md)1|
|[\<uprawnienie >](permission-visual-cpp.md)1|[\<Remarks >](remarks-visual-cpp.md)|[\<returns>](returns-visual-cpp.md)|
|[\<see>](see-visual-cpp.md)1|[\<seealso>](seealso-visual-cpp.md)1|[\<Summary >](summary-visual-cpp.md)|
|[\<value>](value-visual-cpp.md)|||

1. Kompilator sprawdza składnię.

W bieżącej wersji za pomocą kompilatora MSVC obsługuje `<paramref>`, tag, który jest obsługiwany przez inne kompilatory programu Visual Studio. Visual C++ może obsługiwać `<paramref>` w przyszłej wersji.

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)