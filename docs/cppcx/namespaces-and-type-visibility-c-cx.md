---
title: Przestrzenie nazw i widoczność typów (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: cbc01a3a-3b69-4ded-9c42-ecbf0fd0a00e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42457da3c85a73292b836c6da58b17f0341df1be
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102775"
---
# <a name="namespaces-and-type-visibility-ccx-"></a>Przestrzenie nazw i widoczność typów (C + +/ CX)

Przestrzeń nazw jest standardowa konstrukcji języka C++ do grupowania typów powiązanych funkcji i zapobieganie konfliktów nazw w bibliotekach. System typów środowiska wykonawczego Windows wymaga, że wszystkie środowiska uruchomieniowego Windows typy publiczne, łącznie z tymi we własnym kodzie musi być zadeklarowany w przestrzeni nazw w zakresie przestrzeni nazw. Typy publiczne, które są zadeklarowane w zakresie globalnym lub zagnieżdżona w innej klasy spowoduje błąd kompilacji.

Pliku winmd musi mieć taką samą nazwę, który ma głównej przestrzeni nazw. Na przykład klasa, która nosi nazwę A.B.C.MyClass wystąpienia można tworzyć tylko wtedy, gdy jest on zdefiniowany w pliku metadanych, który nosi nazwę A.winmd i A.B.winmd lub A.B.C.winmd. Nazwę pliku wykonywalnego nie musi być zgodna z nazwą pliku .winmd.

## <a name="type-visibility"></a>Widoczność typów

W przestrzeni nazw, typów środowiska wykonawczego Windows — w przeciwieństwie do standardowych typów języka C++ — mieć dostępność prywatnej lub publicznej. Domyślnie dostępność jest prywatny. Publiczny typ jest widoczny w metadanych i dlatego może być używany przez aplikacje i składniki, które mogą być napisane w językach innych niż C++. Ogólnie rzecz biorąc reguły dla typów widocznych są bardziej restrykcyjny niż reguły niewidocznych typów, ponieważ typy widoczne dla nie może ujawnić pojęć specyficznych dla języka C++, które nie są obsługiwane w językach .NET lub JavaScript.

> [!NOTE]
> Metadanych jest używana tylko w czasie wykonywania w językach .NET i języka JavaScript. Gdy C++ aplikacji lub składnika rozmawia innym języku C++ aplikacji lub składnika — w tym Windows składników, które są również zapisywane w języku C++ — ma zużycia czasu wykonywania metadanych jest wymagane.

## <a name="member-accessibility-and-visibility"></a>Ułatwienia dostępu członków i widoczność

W prywatnej klasy ref, interfejsu lub delegata żadnych elementów członkowskich są emitowane do metadanych, nawet jeśli mają one powszechnej dostępności. Klas publicznych ref można kontrolować widoczność elementów członkowskich w metadanych, niezależnie od ich dostępność w kodzie źródłowym. Tak jak w standardowym C++ Zastosuj zasadę najmniejszych uprawnień; Nie wyświetlaj członkom w metadanych, chyba że absolutnie muszą być.

Użyj następujące modyfikatory dostępu, aby kontrolować widoczność metadanych i kod źródłowy w ułatwienia dostępu.

||||
|-|-|-|
|Modyfikator|Znaczenie|Emitowany do metadanych?|
|private|Wartość domyślna dostępu. Takie samo znaczenie jak standardowego języka C++.|Nie|
|protected|Takie samo znaczenie jak w standardzie języka C++ zarówno wewnątrz jednej aplikacji lub składnika, jak i w metadanych.|Tak|
|public|Takie samo znaczenie jak standardowego języka C++.|Tak|
|`public protected` - lub - `protected public`|Chronione ułatwień dostępu w metadanych publicznych w ramach aplikacji lub składnika.|Tak|
|`protected private` lub `private protected`|Nie są widoczne w metadanych; chronione ułatwień dostępu w ramach aplikacji lub składnika.||
|`internal` lub `private public`|Element członkowski jest publiczna w ramach aplikacji lub składnika, ale nie jest widoczny w metadanych.|Nie|

## <a name="windows-runtime-namespaces"></a>Przestrzenie nazw Windows Runtime

Interfejs API Windows składa się z typami, które są zadeklarowane w Windows::\* przestrzeni nazw. Te przestrzenie nazw są zarezerwowane dla Windows i typów nie można dodać do nich. W **przeglądarki obiektów**, możesz wyświetlić te przestrzenie nazw w pliku windows.winmd. Aby uzyskać dokumentację te przestrzenie nazw, zobacz [interfejsu Windows API](https://msdn.microsoft.com/library/windows/apps/br211377).

## <a name="ccx-namespaces"></a>C + +/ CX w przestrzeni nazw

C + +/ CX Definiowanie niektórych typów w tych obszarach nazw jako część projekcji system typów środowiska wykonawczego Windows.

|||
|-|-|
|**Namespace**|**Opis**|
|default|Zawiera wbudowane typy liczbowe i char16. Te typy są w zakresie w każdej przestrzeni nazw i `using` instrukcji nigdy nie jest wymagane.|
|Platforma|Zawiera typy przede wszystkim publiczne, które odpowiadają typów środowiska wykonawczego Windows, takich jak `Array<T>`, `String`, `Guid`, i `Boolean`. Zawiera także typy pomocnika specjalne, takie jak `Platform::Agile<T>` i `Platform::Box<T>`.|
|Platform::Collections|Zawiera klasy konkretnych kolekcji, które implementują interfejsy kolekcji środowiska uruchomieniowego Windows `IVector`, `IMap`i tak dalej. Te typy są definiowane w pliku nagłówkowym, collection.h nie znajduje się w platform.winmd.|
|Platform::details|Zawiera typy, które są używane przez kompilator i nie są przeznaczone do użytku publicznego.|

## <a name="see-also"></a>Zobacz też

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)