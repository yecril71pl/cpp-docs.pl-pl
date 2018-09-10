---
title: Atrybuty interfejsu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 850646e2dda1f226eff7c921dd3fe9f85595ca69
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317657"
---
# <a name="interface-attributes"></a>Atrybuty interfejsu

Następujące atrybuty dotyczą [interfejsu (lub __interface)](../cpp/interface.md) słowa kluczowego języka C++.

|Atrybut|Opis|
|---------------|-----------------|
|[async_uuid](../windows/async-uuid.md)|Określa identyfikator UUID, który określa, że kompilator MIDL, aby zdefiniować synchroniczne i asynchroniczne wersje interfejsu COM.|
|[custom](../windows/custom-cpp.md)|Pozwala zdefiniować własne atrybuty.|
|[dispinterface](../windows/dispinterface.md)|Przełącza interfejsu w pliku .idl, jako interfejs ekspedycji.|
|[dual](../windows/dual.md)|Przełącza interfejsu w pliku .idl, jako podwójnego interfejsu.|
|[export](../windows/export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|
|[helpcontext](../windows/helpcontext.md)|Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w pliku pomocy.|
|[helpfile](../windows/helpfile.md)|Określa nazwę pliku pomocy dla biblioteki typów.|
|[helpstring](../windows/helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany.|
|[helpstringcontext](../windows/helpstringcontext.md)|Określa identyfikator tematu pomocy w pliku hlp lub chm.|
|[helpstringdll](../windows/helpstringdll.md)|Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).|
|[hidden](../windows/hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[library_block](../windows/library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|
|[lokalne](../windows/local-cpp.md)|Umożliwia kompilatorowi MIDL jako generator nagłówka, gdy jest używana w nagłówku interfejsu. W przypadku użycia w poszczególnych funkcji, wyznacza lokalnej procedury, dla którego są generowane nie wycinki.|
|[nonextensible](../windows/nonextensible.md)|Określa, że `IDispatch` wdrożenia zawiera tylko właściwości i metod wymienionych w opisie interfejsu i nie można rozszerzyć za pomocą dodatkowe elementy członkowskie w czasie wykonywania. Ten atrybut jest prawidłowy tylko w [podwójną](../windows/dual.md) interfejsu.|
|[odl](../windows/odl.md)|Identyfikuje interfejs jako interfejs język opisu obiektów (ODL).|
|[object](../windows/object-cpp.md)|Określa niestandardowy interfejs.|
|[oleautomation](../windows/oleautomation.md)|Wskazuje, że interfejs jest zgodna z usługą Automation.|
|[pointer_default](../windows/pointer-default.md)|Określa domyślny atrybut wskaźnik dla wszystkich wskaźników, z wyjątkiem wskaźniki najwyższego poziomu, które pojawiają się listami parametrów.|
|[ptr](../windows/ptr.md)|Określa wskaźnik jako pełna wskaźnika.|
|[restricted](../windows/restricted.md)|Określa, które elementy członkowskie biblioteki nie może być wywoływana arbitralnie.|
|[uuid](../windows/uuid-cpp-attributes.md)|Zawiera unikatowy identyfikator biblioteki|

Musisz przestrzegać tych reguł określających interfejs:

- Domyślna konwencja wywołania jest [__stdcall](../cpp/stdcall.md).

- Identyfikator GUID jest dostarczany za Ciebie, jeśli nie podasz.

- Nie przeciążone metody są dozwolone.

Podczas określania nie [uuid](../windows/uuid-cpp-attributes.md) atrybutu i użycie tej samej nazwy interfejsu, w projektach innego atrybutu, ten sam identyfikator GUID jest generowany.

## <a name="see-also"></a>Zobacz też

[Atrybuty w zależności od zastosowania](../windows/attributes-by-usage.md)