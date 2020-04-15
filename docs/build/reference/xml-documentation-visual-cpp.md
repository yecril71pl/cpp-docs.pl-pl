---
title: Dokumentacja XML (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: c25c54e81bb9c10fc871a2abc178f57e661ae4e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335734"
---
# <a name="xml-documentation-visual-c"></a>Dokumentacja XML (Visual C++)

W języku Visual C++ można dodać komentarze do kodu źródłowego, który będzie przetwarzany do pliku xml. Ten plik może być następnie dane wejściowe do procesu, który tworzy dokumentację dla klas w kodzie.

W pliku kodu języka Visual C++ komentarze dokumentacji XML muszą znajdować się bezpośrednio przed definicją metody lub typu. Komentarze mogą służyć do wypełniania porad danych IntelliSense QuickInfo w następujących scenariuszach:

1. gdy kod jest kompilowany jako składnik środowiska wykonawczego systemu Windows z towarzyszącym plikiem .winmd

1. gdy kod źródłowy znajduje się w bieżącym projekcie

1. w bibliotece, której deklaracje typów i implementacje znajdują się w tym samym pliku nagłówka

> [!NOTE]
> W bieżącym wydaniu komentarze kodu nie są przetwarzane na szablonach lub w czymkolwiek zawierającym typ szablonu (na przykład funkcja przyjmująca parametr jako szablon). Dodanie takich komentarzy spowoduje niezdefiniowane zachowanie.

Aby uzyskać szczegółowe informacje na temat tworzenia pliku xml z komentarzami do dokumentacji, zobacz następujące tematy.

|Aby uzyskać informacje na temat|Zobacz|
|---------------------------|---------|
|Opcje kompilatora do użycia|[/doc](doc-process-documentation-comments-c-cpp.md)|
|Tagi, których można użyć do zapewnienia powszechnie używanych funkcji w dokumentacji|[Zalecane tagi dla komentarzy dokumentacji](recommended-tags-for-documentation-comments-visual-cpp.md)|
|Ciągi identyfikatorów, które kompilator produkuje w celu zidentyfikowania konstrukcji w kodzie|[Przetwarzanie pliku xml](dot-xml-file-processing.md)|
|Jak rozgraniczenie znaczników dokumentacji|[Ograniczniki tagów dokumentacji Visual C++](delimiters-for-visual-cpp-documentation-tags.md)|
|Generowanie pliku xml z jednego lub więcej plików xdc.|[XDCMake — dokumentacja](xdcmake-reference.md)|
|Łącza do informacji o języku XML w odniesieniu do obszarów funkcji programu Visual Studio|[Kod XML w programie Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

Jeśli chcesz umieścić znaki specjalne XML w tekście komentarza dokumentacji, należy użyć jednostek XML lub sekcji CDATA.

## <a name="see-also"></a>Zobacz też

[Component Extensions dla platform środowiska uruchomieniowego](../../extensions/component-extensions-for-runtime-platforms.md)
