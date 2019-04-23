---
title: Atrybuty w zależności od zastosowania
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: f6567a7866516c09bca03fa9f3d3aa5aa997b6b4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038073"
---
# <a name="attributes-by-usage"></a>Atrybuty w zależności od zastosowania

Ten temat zawiera listę atrybutów zgodnie z elementów języka C++, których dotyczą.

Jeśli atrybut poprzedza element, który nie znajduje się w zakresie ten atrybut, blok atrybutu jest traktowany jako komentarz.

|Atrybut|Opis|
|---------------|-----------------|
|[Atrybuty modułów](module-attributes.md)|Dotyczy [modułu](module-cpp.md) atrybutu.|
|[Atrybuty interfejsu](interface-attributes.md)|Dotyczy [__interface](../../cpp/interface.md) C++ — słowo kluczowe.|
|[Atrybuty klasy](class-attributes.md)|Ma zastosowanie do słowa kluczowego języka C++.|
|[Atrybuty metody](method-attributes.md)|Ma zastosowanie do metody w klasie, klasa coclass lub interfejs.|
|[Atrybuty parametru](parameter-attributes.md)|Dotyczy parametry metody w klasie lub interfejsie.|
|[Atrybuty składowych danych](data-member-attributes.md)|Stosuje się do elementów członkowskich danych w klasie, klasa coclass lub interfejs.|
|[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)|Ma zastosowanie do słów kluczowych języka C++.|
|[Atrybuty tablicy](array-attributes.md)|Ma zastosowanie do tablic lub `SAFEARRAY`s.|
|[Oddzielne atrybuty](stand-alone-attributes.md)|Działa bardziej przypominające wiersz kodu, ale nie będzie działać na słowo kluczowe języka C++. Instrukcje autonomicznego atrybutu wymagają średnik na końcu wiersza.|
|[Atrybuty niestandardowe](custom-attributes-cpp.md)|Umożliwia użytkownikowi rozszerzanie metadanych.|

## <a name="module-attributes"></a>Atrybuty modułów
Następujący atrybut będzie stosowany tylko do [modułu](module-cpp.md) atrybutu.

|Atrybut|Opis|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Określa nazwę biblioteki DLL, aby wykonać wyszukiwanie ciągu dokumentu (lokalizacja).|

## <a name="interface-attributes"></a>Atrybuty interfejsu

Następujące atrybuty dotyczą [interfejsu (lub __interface)](../../cpp/interface.md) C++ — słowo kluczowe.

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

## <a name="see-also"></a>Zobacz także

[Atrybuty języka C++ dla modelu COM i platformy .NET](cpp-attributes-com-net.md)<br/>
[Atrybuty według grup](attributes-by-group.md)<br/>
[Alfabetyczny spis atrybutów](attributes-alphabetical-reference.md)