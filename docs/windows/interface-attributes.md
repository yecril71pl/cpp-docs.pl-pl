---
title: Atrybuty interfejsu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ff84939b3211633e199066e1a38da2e91efb1c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="interface-attributes"></a>Atrybuty interfejsu
Następujące atrybuty dotyczą [interfejsu (lub __interface)](../cpp/interface.md) słowa kluczowego języka C++.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[async_uuid](../windows/async-uuid.md)|Określa identyfikator UUID, który określa, że kompilator MIDL, aby zdefiniować synchroniczne i asynchroniczne wersje interfejsu COM.|  
|[niestandardowe](../windows/custom-cpp.md)|Umożliwia określenie własnych atrybutów.|  
|[dispinterface](../windows/dispinterface.md)|Umieszcza interfejsu w pliku .idl jako interfejs wysyłania.|  
|[dual](../windows/dual.md)|Umieszcza interfejsu w pliku .idl jako interfejs podwójny.|  
|[export](../windows/export.md)|Powoduje, że struktura danych mają być umieszczone w pliku .idl.|  
|[helpcontext](../windows/helpcontext.md)|Określa identyfikator kontekstu, która pozwala użytkownikowi oglądać informacje o tym elemencie w pliku pomocy.|  
|[helpfile](../windows/helpfile.md)|Ustawia nazwę pliku pomocy dla biblioteki typów.|  
|[helpstring](../windows/helpstring.md)|Określa ciąg znaków używany do opisania elementu, którego dotyczy.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Określa identyfikator tematu pomocy w formacie pliku .hlp lub .chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).|  
|[hidden](../windows/hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|  
|[library_block](../windows/library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|  
|[lokalne](../windows/local-cpp.md)|Umożliwia przy użyciu kompilatora MIDL jako generator nagłówka w nagłówku interfejsu. W przypadku poszczególnych funkcji wyznacza procedury lokalnym, dla których są generowane nie klas zastępczych.|  
|[nonextensible](../windows/nonextensible.md)|Określa, że `IDispatch` implementacji zawiera tylko właściwości i metod wymienionych w opisie interfejsu i nie może zostać rozszerzony o dodatkowe elementy członkowskie w czasie wykonywania. Ten atrybut jest prawidłowy tylko w [podwójną](../windows/dual.md) interfejsu.|  
|[odl](../windows/odl.md)|Identyfikuje interfejsu jako interfejsu język opisu obiektów (ODL).|  
|[object](../windows/object-cpp.md)|Określa niestandardowy interfejs.|  
|[oleautomation](../windows/oleautomation.md)|Wskazuje, że interfejs jest zgodna z automatyzacji.|  
|[pointer_default](../windows/pointer-default.md)|Określa domyślny atrybut wskaźnik dla wszystkich wskaźników z wyjątkiem wskaźniki najwyższego poziomu, które są wyświetlane na listach parametrem.|  
|[ptr](../windows/ptr.md)|Określa wskaźnik jako pełne wskaźnika.|  
|[restricted](../windows/restricted.md)|Określa, które elementy członkowskie biblioteki nie może być wywoływana arbitralnie.|  
|[Identyfikator UUID](../windows/uuid-cpp-attributes.md)|Zawiera unikatowy identyfikator w bibliotece|  
  
 Należy przestrzegać następujących reguł określających interfejsu:  
  
-   Jest domyślną konwencję wywoływania [__stdcall](../cpp/stdcall.md).  
  
-   Identyfikator GUID jest dostarczany automatycznie, jeśli nie podasz.  
  
-   Żadna metoda przeciążenia są dozwolone.  
  
 Podczas określania nie [uuid](../windows/uuid-cpp-attributes.md) atrybutu i przy użyciu tej samej nazwy interfejsu w projektach inny atrybut, ten sam identyfikator GUID jest generowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty w zależności od zastosowania](../windows/attributes-by-usage.md)