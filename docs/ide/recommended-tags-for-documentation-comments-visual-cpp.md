---
title: Tagi zalecane dla komentarzy do dokumentacji (Visual C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 251baedbf37901a58b34b66b7a10bbdcf5d66557
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564193"
---
# <a name="recommended-tags-for-documentation-comments-visual-c"></a>Tagi zalecane dla komentarzy do dokumentacji (Visual C++)

Kompilator języka Visual C++ będą przetwarzane komentarze dokumentacji w kodzie i tworzy plik .xdc dla każdego compiland — i xdcmake.exe będzie przetwarzać plików xdc do pliku XML. Przetwarzanie pliku XML w celu utworzenia dokumentacji jest szczegółów, który musi zostać wdrożone w lokacji.

Tagi są przetwarzane w konstrukcji, takich jak typy i elementy członkowskie typu.

Tagi musi bezpośrednio poprzedzać typów ani elementów członkowskich.

> [!NOTE]
>  Komentarze dokumentacji nie można zastosować do przestrzeni nazw lub na Brak definicji wiersza dla właściwości i zdarzeń; komentarze dokumentacji musi w deklaracjach w swojej klasie.

Kompilator przetworzy dowolnymi tagami, które jest prawidłowym kodem XML. Następujące znaczniki zawierają powszechnie używanych funkcji w dokumentacji użytkownika:

||||
|-|-|-|
|[\<c >](../ide/c-visual-cpp.md)|[\<Kod >](../ide/code-visual-cpp.md)|[\<przykład >](../ide/example-visual-cpp.md)|
|[\<wyjątek >](../ide/exception-visual-cpp.md)1|[\<obejmują >](../ide/include-visual-cpp.md)1|[\<list>](../ide/list-visual-cpp.md)|
|[\<para >](../ide/para-visual-cpp.md)|[\<param >](../ide/param-visual-cpp.md)1|[\<paramref >](../ide/paramref-visual-cpp.md)1|
|[\<uprawnienie >](../ide/permission-visual-cpp.md)1|[\<Remarks >](../ide/remarks-visual-cpp.md)|[\<Zwraca wartość >](../ide/returns-visual-cpp.md)|
|[\<zobacz >](../ide/see-visual-cpp.md)1|[\<SeeAlso — >](../ide/seealso-visual-cpp.md)1|[\<Summary >](../ide/summary-visual-cpp.md)|
|[\<wartość >](../ide/value-visual-cpp.md)|||

1. Kompilator sprawdza składnię.

W bieżącej wersji kompilatora Visual C++ nie obsługuje `<paramref>`, tag, który jest obsługiwany przez inne kompilatory programu Visual Studio. Visual C++ może obsługiwać `<paramref>` w przyszłej wersji.

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)