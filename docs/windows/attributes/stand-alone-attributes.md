---
title: Oddzielne atrybuty (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: 1183d2b171a25b3b2d1aef14c19f81be65effc6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640830"
---
# <a name="stand-alone-attributes"></a>Oddzielne atrybuty

Autonomicznego atrybutu nie będzie działać na słowo kluczowe języka C++, ale jest kilka dodatkowych wiersza kodu. Instrukcje autonomicznego atrybutu wymagają średnik na końcu wiersza.

## <a name="stand-alone-attribute-list"></a>Lista atrybutów autonomiczny

|Atrybut|Opis|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|Generuje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku nagłówka.|
|[custom](custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[db_command](db-command.md)|Tworzy polecenie OLE DB.|
|[emitidl](emitidl.md)|Określa, czy wszystkie kolejne atrybuty IDL zostanie przetworzone i umieszczony w pliku .idl wygenerowany.|
|[idl_module](idl-module.md)|Określa punkt wejścia w bibliotece DLL.|
|[idl_quote](idl-quote.md)|Umożliwia użycie konstrukcji języka IDL, które nie są obsługiwane w bieżącej wersji programu Visual C++ i mieć przekazywane do pliku .idl wygenerowany.|
|[import](import.md)|Określa innego pliku .idl, .odl — lub .h zawierający definicje, w których ma dotyczyć odwołanie z pliku .idl głównego.|
|[importidl](importidl.md)|Wstawia pliku .idl określony w pliku .idl wygenerowany|
|[importlib](importlib.md)|Sprawia, że typy, które już zostały skompilowane do do biblioteki typów, trwa tworzenie innej biblioteki typów.|
|[include](include-cpp.md)|Określa jeden lub więcej plików nagłówka do uwzględnienia w pliku .idl wygenerowany.|
|[includelib](includelib-cpp.md)|Powoduje, że pliku .idl lub .h, mają zostać uwzględnione w pliku .idl wygenerowany.|
|[library_block](library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|
|[module](module-cpp.md)|Określa blok biblioteki w pliku .idl.|
|[no_injected_text](no-injected-text.md)|Zabezpiecza kompilator przed wprowadzanie kodu w wyniku użycia atrybutu.|
|[pragma](pragma.md)|Generuje określony ciąg bez znaków cudzysłowu do pliku .idl wygenerowany.|

## <a name="see-also"></a>Zobacz też

[Atrybuty w zależności od zastosowania](attributes-by-usage.md)