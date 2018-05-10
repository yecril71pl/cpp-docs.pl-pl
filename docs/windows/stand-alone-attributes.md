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
- attributes [C++], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59846b1ca031cc02c85cb6ace23f96e8c5cc9f37
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="stand-alone-attributes"></a>Oddzielne atrybuty
Atrybut autonomiczny nie będzie działać na słowo kluczowe języka C++, ale jest bardziej przypominają wiersz kodu. Instrukcje atrybutu autonomicznego wymagają średnik na końcu linii.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[cpp_quote](../windows/cpp-quote.md)|Emituje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku nagłówka.|  
|[custom](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[db_command](../windows/db-command.md)|Tworzy polecenia OLE DB.|  
|[emitidl](../windows/emitidl.md)|Określa, czy wszystkie kolejne atrybuty IDL zostanie przetworzona i umieszczony w pliku .idl wygenerowany.|  
|[idl_module](../windows/idl-module.md)|Określa punkt wejścia w bibliotece DLL.|  
|[idl_quote](../windows/idl-quote.md)|Umożliwia użycie konstrukcji języka IDL, które nie są obsługiwane w bieżącej wersji programu Visual C++ i mieć przekazywane do pliku .idl wygenerowany.|  
|[import](../windows/import.md)|Określa innego pliku .idl, .odl — lub .h definicjami, którego ma dotyczyć odwołanie z pliku .idl głównego.|  
|[importidl](../windows/importidl.md)|Wstawia pliku .idl określony w pliku .idl wygenerowany|  
|[importlib](../windows/importlib.md)|Powoduje, że typy, które już zostały skompilowane w innej bibliotece typu dostępne do tworzenia biblioteki typów.|  
|[include](../windows/include-cpp.md)|Określa co najmniej jeden plik nagłówka do uwzględnienia w pliku .idl wygenerowany.|  
|[includelib —](../windows/includelib-cpp.md)|Powoduje, że pliku .idl lub .h do uwzględnienia w pliku .idl wygenerowany.|  
|[library_block](../windows/library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|  
|[Moduł](../windows/module-cpp.md)|Określa blok biblioteki w pliku .idl.|  
|[no_injected_text](../windows/no-injected-text.md)|Zabezpiecza kompilator przed wstrzyknięcie kodu w wyniku użycia atrybutu.|  
|[pragma](../windows/pragma.md)|Emituje określony ciąg bez znaków cudzysłowu do pliku .idl wygenerowany.|  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty w zależności od zastosowania](../windows/attributes-by-usage.md)