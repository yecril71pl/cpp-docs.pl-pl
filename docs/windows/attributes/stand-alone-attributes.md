---
title: Atrybuty autonomiczne (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: a7df91bbb1c6929b08d8cd867be9f13ce0c35b91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166175"
---
# <a name="stand-alone-attributes"></a>Oddzielne atrybuty

Atrybut autonomiczny nie działa na słowie kluczowym C++ , ale jest bardziej podobny do wiersza kodu. Autonomiczne instrukcje atrybutów wymagają średnika na końcu wiersza.

## <a name="stand-alone-attribute-list"></a>Lista atrybutów autonomicznych

|Atrybut|Opis|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Emituje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku nagłówkowego.|
|[custom](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[db_command](db-command.md)|Tworzy polecenie OLE DB.|
|[emitidl](emitidl.md)|Określa, czy wszystkie kolejne atrybuty IDL będą przetwarzane i umieszczane w wygenerowanym pliku IDL.|
|[idl_module](idl-module.md)|Określa punkt wejścia w bibliotece DLL.|
|[idl_quote](idl-quote.md)|Umożliwia korzystanie z konstrukcji IDL, które nie są obsługiwane w bieżącej wersji wizualizacji C++ i są przekazywane do wygenerowanego pliku IDL.|
|[import](import.md)|Określa inny plik IDL,. ODL lub. h zawierający definicje, które chcesz odwołać z głównego pliku. idl.|
|[importidl](importidl.md)|Wstawia określony plik IDL do wygenerowanego pliku IDL|
|[importlib](importlib.md)|Sprawia, że typy, które zostały już skompilowane w innej bibliotece typów dostępne dla tworzonej biblioteki typów.|
|[include](include-cpp.md)|Określa co najmniej jeden plik nagłówka do uwzględnienia w wygenerowanym pliku IDL.|
|[includelib](includelib-cpp.md)|Powoduje, że plik IDL lub h zostanie uwzględniony w wygenerowanym pliku IDL.|
|[library_block](library-block.md)|Umieszcza konstrukcję w bloku biblioteki pliku IDL.|
|[module](module-cpp.md)|Definiuje blok biblioteki w pliku IDL.|
|[no_injected_text](no-injected-text.md)|Uniemożliwia kompilatorowi wstrzyknięcie kodu w wyniku użycia atrybutów.|
|[pragma](pragma.md)|Emituje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku IDL.|

## <a name="see-also"></a>Zobacz też

[Atrybuty w zależności od zastosowania](attributes-by-usage.md)
