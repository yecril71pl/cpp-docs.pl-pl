---
title: Atrybuty interfejsu (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
ms.openlocfilehash: d954b7622ac78142c84b40007ecda8138b1b8f2f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556650"
---
# <a name="interface-attributes"></a>Atrybuty interfejsu

Następujące atrybuty dotyczą [interfejsu (lub __interface)](../../cpp/interface.md) słowa kluczowego języka C++.

|Atrybut|Opis|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Określa identyfikator UUID, który określa, że kompilator MIDL, aby zdefiniować synchroniczne i asynchroniczne wersje interfejsu COM.|
|[custom](custom-cpp.md)|Pozwala zdefiniować własne atrybuty.|
|[dispinterface](dispinterface.md)|Przełącza interfejsu w pliku .idl, jako interfejs ekspedycji.|
|[dual](dual.md)|Przełącza interfejsu w pliku .idl, jako podwójnego interfejsu.|
|[export](export.md)|Powoduje to struktura danych, należy umieścić w pliku .idl.|
|[helpcontext](helpcontext.md)|Określa identyfikator kontekstu, który pozwala użytkownikowi oglądać informacje o tym elemencie w pliku pomocy.|
|[helpfile](helpfile.md)|Określa nazwę pliku pomocy dla biblioteki typów.|
|[helpstring](helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do której jest stosowany.|
|[helpstringcontext](helpstringcontext.md)|Określa identyfikator tematu pomocy w pliku hlp lub chm.|
|[helpstringdll](helpstringdll.md)|Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).|
|[hidden](hidden.md)|Wskazuje, czy element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[library_block](library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|
|[local](local-cpp.md)|Umożliwia kompilatorowi MIDL jako generator nagłówka, gdy jest używana w nagłówku interfejsu. W przypadku użycia w poszczególnych funkcji, wyznacza lokalnej procedury, dla którego są generowane nie wycinki.|
|[nonextensible](nonextensible.md)|Określa, że `IDispatch` wdrożenia zawiera tylko właściwości i metod wymienionych w opisie interfejsu i nie można rozszerzyć za pomocą dodatkowe elementy członkowskie w czasie wykonywania. Ten atrybut jest prawidłowy tylko w [podwójną](dual.md) interfejsu.|
|[odl](odl.md)|Identyfikuje interfejs jako interfejs język opisu obiektów (ODL).|
|[object](object-cpp.md)|Określa niestandardowy interfejs.|
|[oleautomation](oleautomation.md)|Wskazuje, że interfejs jest zgodna z usługą Automation.|
|[pointer_default](pointer-default.md)|Określa domyślny atrybut wskaźnik dla wszystkich wskaźników, z wyjątkiem wskaźniki najwyższego poziomu, które pojawiają się listami parametrów.|
|[ptr](ptr.md)|Określa wskaźnik jako pełna wskaźnika.|
|[restricted](restricted.md)|Określa, które elementy członkowskie biblioteki nie może być wywoływana arbitralnie.|
|[uuid](uuid-cpp-attributes.md)|Zawiera unikatowy identyfikator biblioteki|

Musisz przestrzegać tych reguł określających interfejs:

- Domyślna konwencja wywołania jest [__stdcall](../../cpp/stdcall.md).

- Identyfikator GUID jest dostarczany za Ciebie, jeśli nie podasz.

- Nie przeciążone metody są dozwolone.

Podczas określania nie [uuid](uuid-cpp-attributes.md) atrybutu i użycie tej samej nazwy interfejsu, w projektach innego atrybutu, ten sam identyfikator GUID jest generowany.

## <a name="see-also"></a>Zobacz też

[Atrybuty w zależności od zastosowania](attributes-by-usage.md)