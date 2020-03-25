---
title: Atrybuty w zależności od zastosowania
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: fd5c5826b4119409dd288d0587c3e53a7d3f3aab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167397"
---
# <a name="attributes-by-usage"></a>Atrybuty w zależności od zastosowania

Ten temat zawiera listę atrybutów według elementów C++ języka, do których mają zastosowanie.

Jeśli atrybut poprzedza element, który nie znajduje się w zakresie atrybutu, blok atrybutu jest traktowany jako komentarz.

|Atrybut|Opis|
|---------------|-----------------|
|[Atrybuty modułów](module-attributes.md)|Dotyczy atrybutu [modułu](module-cpp.md) .|
|[Atrybuty interfejsu](interface-attributes.md)|Dotyczy słowa kluczowego [__interface](../../cpp/interface.md) C++ .|
|[Atrybuty klasy](class-attributes.md)|Stosuje się do C++ słowa kluczowego.|
|[Atrybuty metody](method-attributes.md)|Dotyczy metod w klasie, klasie coclass lub interfejsie.|
|[Atrybuty parametru](parameter-attributes.md)|Dotyczy parametrów metody w klasie lub interfejsie.|
|[Atrybuty składowych danych](data-member-attributes.md)|Dotyczy składowych danych w klasie, klasie lub interfejsie.|
|[Atrybuty Typedef, Enum, Union oraz Struct](typedef-enum-union-and-struct-attributes.md)|Stosuje się do C++ słów kluczowych.|
|[Atrybuty tablicy](array-attributes.md)|Dotyczy tablic lub `SAFEARRAY`s.|
|[Oddzielne atrybuty](stand-alone-attributes.md)|Działa podobnie jak wiersz kodu, ale nie działa na C++ słowie kluczowym. Autonomiczne instrukcje atrybutów wymagają średnika na końcu wiersza.|
|[Atrybuty niestandardowe](custom-attributes-cpp.md)|Zezwala użytkownikowi na rozszerzonie metadanych.|

## <a name="module-attributes"></a>Atrybuty modułów
Następujący atrybut może być stosowany tylko do atrybutu [modułu](module-cpp.md) .

|Atrybut|Opis|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Określa nazwę biblioteki DLL, która ma być używana do przeszukiwania ciągu dokumentu (lokalizacja).|

## <a name="interface-attributes"></a>Atrybuty interfejsu

Następujące atrybuty dotyczą słowa kluczowego [Interface (lub __interface)](../../cpp/interface.md) C++ .

|Atrybut|Opis|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Określa identyfikator UUID, który kieruje kompilator MIDL do definiowania synchronicznych i asynchronicznych wersji interfejsu COM.|
|[custom](custom-cpp.md)|Umożliwia zdefiniowanie własnych atrybutów.|
|[dispinterface](dispinterface.md)|Umieszcza interfejs w pliku. idl jako interfejs wysyłania.|
|[dual](dual.md)|Umieszcza interfejs w pliku. idl jako podwójny interfejs.|
|[export](export.md)|Powoduje, że struktura danych zostanie umieszczona w pliku IDL.|
|[helpcontext](helpcontext.md)|Określa identyfikator kontekstu, który umożliwia użytkownikowi wyświetlanie informacji o tym elemencie w pliku pomocy.|
|[helpfile](helpfile.md)|Ustawia nazwę pliku pomocy dla biblioteki typów.|
|[helpstring](helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do którego ma zastosowanie.|
|[helpstringcontext](helpstringcontext.md)|Określa identyfikator tematu pomocy w pliku HLP lub chm.|
|[helpstringdll](helpstringdll.md)|Określa nazwę biblioteki DLL, która ma być używana do przeszukiwania ciągu dokumentu (lokalizacja).|
|[hidden](hidden.md)|Wskazuje, że element istnieje, ale nie powinien być wyświetlany w przeglądarce zorientowanej na użytkownika.|
|[library_block](library-block.md)|Umieszcza konstrukcję w bloku biblioteki pliku IDL.|
|[local](local-cpp.md)|Umożliwia użycie kompilatora MIDL jako generatora nagłówka, gdy jest używany w nagłówku interfejsu. W przypadku użycia w pojedynczej funkcji określa procedurę lokalną, dla której nie są generowane żadne wycinki.|
|[nonextensible](nonextensible.md)|Określa, że implementacja `IDispatch` zawiera tylko właściwości i metody wymienione w opisie interfejsu i nie można jej rozszerzyć z dodatkowymi elementami członkowskimi w czasie wykonywania. Ten atrybut jest prawidłowy tylko w [podwójnym](dual.md) interfejsie.|
|[odl](odl.md)|Identyfikuje interfejs jako interfejs ODL (Object Description Language).|
|[object](object-cpp.md)|Identyfikuje niestandardowy interfejs.|
|[oleautomation](oleautomation.md)|Wskazuje, że interfejs jest zgodny z automatyzacją.|
|[pointer_default](pointer-default.md)|Określa domyślny atrybut wskaźnika dla wszystkich wskaźników oprócz wskaźników najwyższego poziomu, które są wyświetlane na listach parametrów.|
|[ptr](ptr.md)|Wyznacza wskaźnik jako pełny wskaźnik.|
|[restricted](restricted.md)|Określa, które elementy członkowskie biblioteki nie mogą być wywoływane arbitralnie.|
|[uuid](uuid-cpp-attributes.md)|Zapewnia unikatowy identyfikator biblioteki|

Aby zdefiniować interfejs, należy przestrzegać następujących zasad:

- Domyślna konwencja wywoływania to [__stdcall](../../cpp/stdcall.md).

- Identyfikator GUID jest dostarczany dla Ciebie, jeśli nie zostanie podany.

- Nie są dozwolone żadne przeciążone metody.

Jeśli nie określisz atrybutu [UUID](uuid-cpp-attributes.md) i używasz tej samej nazwy interfejsu w różnych projektach atrybutów, generowany jest ten sam identyfikator GUID.

## <a name="see-also"></a>Zobacz też

[Atrybuty języka C++ dla modelu COM i platformy .NET](cpp-attributes-com-net.md)<br/>
[Atrybuty według grup](attributes-by-group.md)<br/>
[Alfabetyczny spis atrybutów](attributes-alphabetical-reference.md)
