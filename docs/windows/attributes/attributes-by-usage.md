---
title: Atrybuty w zależności od zastosowania
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: dcbed019f8cd08ddbf4ab6b4756a59f7fcbabc4b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361336"
---
# <a name="attributes-by-usage"></a>Atrybuty w zależności od zastosowania

W tym temacie wymieniono atrybuty zgodnie z elementami języka C++, do których mają zastosowanie.

Jeśli atrybut poprzedza element, który nie znajduje się w zakresie atrybutu, blok atrybutów jest traktowany jako komentarz.

|Atrybut|Opis|
|---------------|-----------------|
|[Atrybuty modułów](module-attributes.md)|Dotyczy atrybutu [modułu.](module-cpp.md)|
|[Atrybuty interfejsu](interface-attributes.md)|Dotyczy słowa [kluczowego __interface](../../cpp/interface.md) C++.|
|[Atrybuty klasy](class-attributes.md)|Dotyczy słowa kluczowego C++.|
|[Atrybuty metody](method-attributes.md)|Dotyczy metod w klasie, coclass lub interfejsie.|
|[Atrybuty parametrów](parameter-attributes.md)|Dotyczy parametrów metody w klasie lub interfejsie.|
|[Atrybuty elementów członkowskich danych](data-member-attributes.md)|Dotyczy elementów członkowskich danych w klasie, coclass lub interfejsie.|
|[Atrybuty Typedef, Enum, Union i Struct](typedef-enum-union-and-struct-attributes.md)|Dotyczy słów kluczowych języka C++.|
|[Atrybuty tablicy](array-attributes.md)|Dotyczy tablic lub `SAFEARRAY`s.|
|[Atrybuty autonomiczne](stand-alone-attributes.md)|Działa bardziej jak wiersz kodu, ale nie działa na c++ słowa kluczowego. Instrukcje atrybutów autonomicznych wymagają średnika na końcu wiersza.|
|[Atrybuty niestandardowe](custom-attributes-cpp.md)|Umożliwia użytkownikowi rozszerzenie metadanych.|

## <a name="module-attributes"></a>Atrybuty modułów

Poniższy atrybut można zastosować tylko do atrybutu [modułu.](module-cpp.md)

|Atrybut|Opis|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Określa nazwę biblioteki DLL, która ma być używana do odnoślenia ciągu dokumentu (lokalizacja).|

## <a name="interface-attributes"></a>Atrybuty interfejsu

Następujące atrybuty dotyczą słowa kluczowego [interfejsu (lub __interface)](../../cpp/interface.md) języka C++.

|Atrybut|Opis|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Określa identyfikator UUID, który kieruje kompilator MIDL do definiowania zarówno synchronicznych, jak i asynchronicznych wersji interfejsu COM.|
|[Niestandardowe](custom-cpp.md)|Umożliwia definiowanie własnych atrybutów.|
|[dispinterface](dispinterface.md)|Umieszcza interfejs w pliku .idl jako interfejs wysyłki.|
|[dual](dual.md)|Umieszcza interfejs w pliku .idl jako podwójny interfejs.|
|[Eksportu](export.md)|Powoduje, że struktura danych ma zostać umieszczona w pliku .idl.|
|[helpcontext](helpcontext.md)|Określa identyfikator kontekstu, który umożliwia użytkownikowi wyświetlanie informacji o tym elemencie w pliku Pomocy.|
|[helpfile](helpfile.md)|Ustawia nazwę pliku Pomocy dla biblioteki typów.|
|[helpstring](helpstring.md)|Określa ciąg znaków, który jest używany do opisania elementu, do którego ma zastosowanie.|
|[helpstringcontext](helpstringcontext.md)|Określa identyfikator tematu pomocy w pliku .hlp lub .chm.|
|[helpstringdll](helpstringdll.md)|Określa nazwę biblioteki DLL, która ma być używana do odnoślenia ciągu dokumentu (lokalizacja).|
|[Ukryte](hidden.md)|Wskazuje, że element istnieje, ale nie powinny być wyświetlane w przeglądarce zorientowanej na użytkownika.|
|[library_block](library-block.md)|Umieszcza konstrukcję wewnątrz bloku biblioteki pliku .idl.|
|[Lokalnych](local-cpp.md)|Umożliwia użycie kompilatora MIDL jako generatora nagłówka, gdy jest używany w nagłówku interfejsu. W przypadku użycia w poszczególnych funkcji, wyznacza procedurę lokalną, dla której nie są generowane żadne wycinki.|
|[nonextensible](nonextensible.md)|Określa, że `IDispatch` implementacja zawiera tylko właściwości i metody wymienione w opisie interfejsu i nie można jej rozszerzyć o dodatkowe elementy członkowskie w czasie wykonywania. Ten atrybut jest prawidłowy tylko w [interfejsie dualnym.](dual.md)|
|[odl](odl.md)|Identyfikuje interfejs jako interfejs języka opisu obiektu (ODL).|
|[obiekt](object-cpp.md)|Identyfikuje interfejs niestandardowy.|
|[oleautomation](oleautomation.md)|Wskazuje, że interfejs jest zgodny z automatyzacji.|
|[pointer_default](pointer-default.md)|Określa domyślny atrybut wskaźnika dla wszystkich wskaźników z wyjątkiem wskaźników najwyższego poziomu, które pojawiają się na listach parametrów.|
|[Ptr](ptr.md)|Wyznacza wskaźnik jako pełny wskaźnik.|
|[restricted](restricted.md)|Określa, których członków biblioteki nie można wywołać dowolnie.|
|[uuid](uuid-cpp-attributes.md)|Udostępnia unikatowy identyfikator biblioteki|

Należy przestrzegać tych reguł podczas definiowania interfejsu:

- Domyślna konwencja wywoływania to [__stdcall](../../cpp/stdcall.md).

- Identyfikator GUID jest dostarczany dla Ciebie, jeśli go nie podasz.

- Nie są dozwolone przeciążone metody.

Gdy nie określa się [atrybutu uuid](uuid-cpp-attributes.md) i przy użyciu tej samej nazwy interfejsu w różnych projektach atrybutów, generowany jest ten sam identyfikator GUID.

## <a name="see-also"></a>Zobacz też

[Atrybuty języka C++ dla modelu COM i platformy .NET](cpp-attributes-com-net.md)<br/>
[Atrybuty według grupy](attributes-by-group.md)<br/>
[Atrybuty Odwołanie alfabetyczne](attributes-alphabetical-reference.md)
