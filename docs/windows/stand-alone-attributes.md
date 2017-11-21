---
title: Oddzielne atrybuty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- standalone attributes
- attributes [C++], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 17009c1e9c1f7a771b717a96d1aadc4a680fe78f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="stand-alone-attributes"></a>Oddzielne atrybuty
Atrybut autonomiczny nie będzie działać na słowo kluczowe języka C++, ale jest bardziej przypominają wiersz kodu. Instrukcje atrybutu autonomicznego wymagają średnik na końcu linii.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[cpp_quote —](../windows/cpp-quote.md)|Emituje określony ciąg bez znaków cudzysłowu do wygenerowanego pliku nagłówka.|  
|[niestandardowe](../windows/custom-cpp.md)|Umożliwia zdefiniowanie własnego atrybutu.|  
|[db_command —](../windows/db-command.md)|Tworzy polecenia OLE DB.|  
|[emitidl](../windows/emitidl.md)|Określa, czy wszystkie kolejne atrybuty IDL zostanie przetworzona i umieszczony w pliku .idl wygenerowany.|  
|[idl_module](../windows/idl-module.md)|Określa punkt wejścia w bibliotece DLL.|  
|[idl_quote —](../windows/idl-quote.md)|Umożliwia użycie konstrukcji języka IDL, które nie są obsługiwane w bieżącej wersji programu Visual C++ i mieć przekazywane do pliku .idl wygenerowany.|  
|[Import](../windows/import.md)|Określa innego pliku .idl, .odl — lub .h definicjami, którego ma dotyczyć odwołanie z pliku .idl głównego.|  
|[importidl —](../windows/importidl.md)|Wstawia pliku .idl określony w pliku .idl wygenerowany|  
|[importlib](../windows/importlib.md)|Powoduje, że typy, które już zostały skompilowane w innej bibliotece typu dostępne do tworzenia biblioteki typów.|  
|[obejmują](../windows/include-cpp.md)|Określa co najmniej jeden plik nagłówka do uwzględnienia w pliku .idl wygenerowany.|  
|[includelib —](../windows/includelib-cpp.md)|Powoduje, że pliku .idl lub .h do uwzględnienia w pliku .idl wygenerowany.|  
|[library_block —](../windows/library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|  
|[Moduł](../windows/module-cpp.md)|Określa blok biblioteki w pliku .idl.|  
|[no_injected_text](../windows/no-injected-text.md)|Zabezpiecza kompilator przed wstrzyknięcie kodu w wyniku użycia atrybutu.|  
|[Wartość dyrektywy pragma](../windows/pragma.md)|Emituje określony ciąg bez znaków cudzysłowu do pliku .idl wygenerowany.|  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty w zależności od użycia](../windows/attributes-by-usage.md)