---
title: Oddzielne atrybuty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c44223dad2ac4d6306bf3896cd8ec7be84a5a2b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407767"
---
# <a name="stand-alone-attributes"></a>Oddzielne atrybuty
Autonomicznego atrybutu nie będzie działać na słowo kluczowe języka C++, ale jest kilka dodatkowych wiersza kodu. Instrukcje autonomicznego atrybutu wymagają średnik na końcu wiersza.
  
|Atrybut|Opis|
|---------------|-----------------|
|[cpp_quote](../windows/cpp-quote.md)|Generuje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku nagłówka.|
|[custom](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|
|[db_command](../windows/db-command.md)|Tworzy polecenie OLE DB.|
|[emitidl](../windows/emitidl.md)|Określa, czy wszystkie kolejne atrybuty IDL zostanie przetworzone i umieszczony w pliku .idl wygenerowany.|
|[idl_module](../windows/idl-module.md)|Określa punkt wejścia w bibliotece DLL.|
|[idl_quote](../windows/idl-quote.md)|Umożliwia użycie konstrukcji języka IDL, które nie są obsługiwane w bieżącej wersji programu Visual C++ i mieć przekazywane do pliku .idl wygenerowany.|
|[import](../windows/import.md)|Określa innego pliku .idl, .odl — lub .h zawierający definicje, w których ma dotyczyć odwołanie z pliku .idl głównego.|
|[importidl](../windows/importidl.md)|Wstawia pliku .idl określony w pliku .idl wygenerowany|
|[importlib](../windows/importlib.md)|Sprawia, że typy, które już zostały skompilowane do do biblioteki typów, trwa tworzenie innej biblioteki typów.|
|[include](../windows/include-cpp.md)|Określa jeden lub więcej plików nagłówka do uwzględnienia w pliku .idl wygenerowany.|
|[includelib —](../windows/includelib-cpp.md)|Powoduje, że pliku .idl lub .h, mają zostać uwzględnione w pliku .idl wygenerowany.|
|[library_block](../windows/library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|
|[Moduł](../windows/module-cpp.md)|Określa blok biblioteki w pliku .idl.|
|[no_injected_text](../windows/no-injected-text.md)|Zabezpiecza kompilator przed wprowadzanie kodu w wyniku użycia atrybutu.|
|[pragma](../windows/pragma.md)|Generuje określony ciąg bez znaków cudzysłowu do pliku .idl wygenerowany.|
  
## <a name="see-also"></a>Zobacz też

[Atrybuty w zależności od zastosowania](../windows/attributes-by-usage.md)