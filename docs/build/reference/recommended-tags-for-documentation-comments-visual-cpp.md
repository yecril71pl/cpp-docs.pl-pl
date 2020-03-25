---
title: Tagi zalecane dla komentarzy do dokumentacjiC++ (Komentarze do dokumentacji)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 4e0937b79012f65ba136e18ac81f014be23688f8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168866"
---
# <a name="recommended-tags-for-documentation-comments"></a>Zalecane tagi przeznaczone do komentarzy dokumentacji

Kompilator MSVC będzie przetwarzać komentarze dokumentacji w kodzie i tworzy plik. xdc dla każdego jednostka kompilacji, a xdcmake. exe będzie przetwarzać pliki. xdc do pliku. XML. Przetwarzanie pliku. XML w celu utworzenia dokumentacji jest szczegółami, które muszą zostać zaimplementowane w Twojej lokacji.

Tagi są przetwarzane na konstrukcjach, takich jak typy i elementy członkowskie typu.

Tagi muszą występować bezpośrednio przed typami lub elementami członkowskimi.

> [!NOTE]
>  Komentarzy do dokumentacji nie można zastosować do przestrzeni nazw lub w definicji poza wierszem dla właściwości i zdarzeń; Komentarze dokumentacji muszą być zgodne z deklaracjami w klasie.

Kompilator będzie przetwarzać dowolny tag, który jest prawidłowym kodem XML. Poniższe Tagi zapewniają powszechnie używane funkcje w dokumentacji użytkownika:

||||
|-|-|-|
|[\<c >](c-visual-cpp.md)|[> kodu \<](code-visual-cpp.md)|[przykład \<>](example-visual-cpp.md)|
|[\<wyjątek >](exception-visual-cpp.md)1|[\<uwzględnij >](include-visual-cpp.md)1|[> Lista \<](list-visual-cpp.md)|
|[\<para >](para-visual-cpp.md)|[\<param >](param-visual-cpp.md)1|[\<paramref >](paramref-visual-cpp.md)1|
|[> uprawnień\<](permission-visual-cpp.md)1|[\<uwagi >](remarks-visual-cpp.md)|[\<returns>](returns-visual-cpp.md)|
|[\<zobacz >](see-visual-cpp.md)1|[\<seealso — >](seealso-visual-cpp.md)1|[\<summary>](summary-visual-cpp.md)|
|[\<value>](value-visual-cpp.md)|||

1. Kompilator weryfikuje składnię.

W bieżącej wersji kompilator MSVC nie obsługuje `<paramref>`, tag, który jest obsługiwany przez inne kompilatory programu Visual Studio. Wizualizacja C++ może obsługiwać `<paramref>` w przyszłej wersji.

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](xml-documentation-visual-cpp.md)
