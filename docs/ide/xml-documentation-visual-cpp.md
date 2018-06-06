---
title: Plik dokumentacji XML (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d763a62edc2f21d8a7669e409c164906c440f1d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705637"
---
# <a name="xml-documentation-visual-c"></a>Dokumentacja XML (Visual C++)
W programie Visual C++ komentarze można dodawać do kodu źródłowego, które będą przetwarzane do pliku XML. Ten plik można następnie dane wejściowe do procesu, który tworzy dokumentację dla klas w kodzie.  
  
 W pliku kodu Visual C++ komentarze dokumentacji XML muszą być znajduje się bezpośrednio przed definicją metody lub typu. Komentarze mogą służyć do wypełnienia Porada danych skrócone informacje funkcji IntelliSense w następujących scenariuszach:  
  
1.  Jeśli kod jest skompilowana jako składnik środowiska wykonawczego systemu Windows przy użyciu towarzyszący plik winmd  
  
2.  Jeśli kod źródłowy znajduje się w bieżącym projekcie  
  
3.  w bibliotece, których implementacji i deklaracje typu znajdują się w tym samym pliku nagłówka  
  
> [!NOTE]
>  W bieżącej wersji na szablony lub jakikolwiek zawierający typ szablonu (na przykład funkcja biorąc parametr jako szablon) nie są przetwarzane komentarze w kodzie. Dodawanie komentarzy takie spowoduje niezdefiniowane zachowanie.  
  
 Aby uzyskać więcej informacji na temat tworzenia pliku XML z komentarzy do dokumentacji zobacz następujące tematy.  
  
|Aby uzyskać informacje na temat|Zobacz|  
|---------------------------|---------|  
|Opcje kompilatora do użycia|[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
|Znaczniki służy do zapewnienia najczęściej używane funkcje w dokumentacji|[Zalecane tagi przeznaczone do komentarzy dokumentacji](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|  
|Ciągi identyfikatorów, które kompilator generuje do identyfikowania konstrukcje w kodzie|[Przetwarzanie pliku XML](../ide/dot-xml-file-processing.md)|  
|Jak ograniczyć tagów dokumentacji|[Ograniczniki tagów dokumentacji Visual C++](../ide/delimiters-for-visual-cpp-documentation-tags.md)|  
|Generowanie pliku XML z jednego lub więcej plików xdc.|[XDCMake — dokumentacja](../ide/xdcmake-reference.md)|  
|Linki do informacji dotyczących XML, ponieważ odnosi się do obszarów funkcji programu Visual Studio|[Kod XML w Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|  
  
 Jeśli trzeba umieścić specjalne znaki XML w tekście komentarza do dokumentacji, należy użyć jednostki XML lub sekcji CDATA.  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)