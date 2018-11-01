---
title: Dokumentacja XML (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: 380fe73bba71d08bb9315e218f5946a7cf935108
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523889"
---
# <a name="xml-documentation-visual-c"></a>Dokumentacja XML (Visual C++)

W programie Visual C++ możesz dodać komentarze do kodu źródłowego, które będą przetwarzane do pliku XML. Ten plik może być następnie dane wejściowe do procesu, który tworzy dokumentację dla klasy w kodzie.

W pliku z kodem języka Visual C++ komentarze dokumentacji XML muszą być bezpośrednio przed definicją metody lub typu. Komentarze może służyć do wypełniania Porada danych skrócone informacje funkcji IntelliSense w następujących scenariuszach:

1. gdy kod jest kompilowany jako składnik środowiska uruchomieniowego Windows przy użyciu towarzyszącego pliku .winmd

1. Jeśli kod źródłowy znajduje się w bieżącym projekcie

1. w bibliotece, których typ deklaracje i implementacje znajdują się w tym samym pliku nagłówka

> [!NOTE]
>  W bieżącej wersji szablonów lub cokolwiek zawierający typ szablonu (na przykład funkcja przyjmująca parametr jako szablon) nie są przetwarzane komentarze w kodzie. Dodawanie takich uwag spowoduje niezdefiniowane zachowanie.

Aby uzyskać szczegółowe informacje na temat tworzenia pliku XML z komentarzami dokumentacji zobacz następujące tematy.

|Aby uzyskać informacje na temat|Zobacz|
|---------------------------|---------|
|Opcje kompilatora do użycia|[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|
|Tagi, używane w celu zapewnienia często używane funkcje w dokumentacji|[Zalecane tagi przeznaczone do komentarzy dokumentacji](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|
|Ciągi identyfikatorów, które kompilator generuje do identyfikowania konstrukcje w kodzie|[Przetwarzanie pliku XML](../ide/dot-xml-file-processing.md)|
|Jak ograniczyć tagów dokumentacji|[Ograniczniki tagów dokumentacji Visual C++](../ide/delimiters-for-visual-cpp-documentation-tags.md)|
|Trwa generowanie pliku XML z jednego lub więcej plików xdc.|[XDCMake — dokumentacja](../ide/xdcmake-reference.md)|
|Łącza do informacji o XML, jak to odnosi się do obszarów funkcji programu Visual Studio|[XML w programie Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

Jeśli musisz umieścić specjalne znaki XML w tekście komentarza do dokumentacji, należy użyć jednostki XML lub sekcji CDATA.

## <a name="see-also"></a>Zobacz też

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)