---
title: Obszary nazw i typ widoczności (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: cbc01a3a-3b69-4ded-9c42-ecbf0fd0a00e
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 07b48d0464dfc36f671f6566ce45894aca76cbc4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089835"
---
# <a name="namespaces-and-type-visibility-ccx-"></a>Obszary nazw i typ widoczności (C + +/ CX)
Przestrzeń nazw jest standardowa konstrukcja C++ do grupowania typów, które ma funkcje związane z a zapobiegania konflikty nazw w bibliotekach. System typów środowiska wykonawczego systemu Windows wymaga, aby wszystkich publicznych typów środowiska wykonawczego systemu Windows, włącznie z zawartymi w swoim własnym kodem musi być zadeklarowana w przestrzeni nazw w zakresie przestrzeni nazw. Typy publiczne, które są zadeklarowane w zakresie globalnym lub zagnieżdżona w innej klasy spowoduje błąd w czasie kompilacji.  
  
 Plik winmd musi mieć takiej samej nazwie, który ma głównej przestrzeni nazw. Na przykład klasy o nazwie A.B.C.MyClass można wdrożyć tylko wtedy, gdy jest on zdefiniowany w pliku metadanych o nazwie A.winmd lub A.B.winmd lub A.B.C.winmd. Nazwa pliku wykonywalnego nie musi być zgodna z nazwą pliku winmd.  
  
## <a name="type-visibility"></a>Widoczność typów  
 W obszarze nazw, typów środowiska wykonawczego systemu Windows — w przeciwieństwie do standardowych typów języka C++ — mieć dostępność prywatny lub publiczny. Domyślnie dostępność jest prywatny. Publiczny typ jest widoczny dla metadanych i dlatego jest dostępne z aplikacji i składników, które mogą być napisane w językach innych niż C++. Ogólnie rzecz biorąc zasady typy widoczne są bardziej restrykcyjny niż reguły dla typów niewidoczne, ponieważ typy widoczne nie może ujawnić pojęcia specyficzne dla języka C++, które nie są obsługiwane w językach .NET lub JavaScript.  
  
> [!NOTE]
>  Metadanych jest używany tylko w czasie wykonywania, języków .NET i JavaScript. Gdy C++ aplikację lub składnik rozmawia kolejną C++ aplikacji lub składnika — obejmuje składniki systemu Windows, które są wszystkie napisane w języku C++ — nie zużycie czasu wykonywania metadanych jest wymagane.  
  
## <a name="member-accessibility-and-visibility"></a>Dostępność elementu członkowskiego i widoczność  
 W prywatnej klasy ref, interfejsem ani obiektem delegowanym żadnych elementów członkowskich są emitowane metadanych, nawet jeśli ma powszechnej dostępności. W klasach publicznego ref można kontrolować widoczności elementów członkowskich w metadanych, niezależnie od ich dostępności w kodzie źródłowym. Jak standard C++ Zastosuj zasadą najniższych uprawnień; Nie wyświetlaj członkowie w metadanych, chyba że absolutnie muszą być.  
  
 Użyj następujących modyfikatorów dostępu, aby kontrolować zarówno widoczność metadanych i dostępności kodu źródłowego.  
  
||||  
|-|-|-|  
|Modyfikator|Znaczenie|Wysyłanego do metadanych?|  
|private|Dostępność domyślne. Takie samo znaczenie jak standardu C++.|Nie|  
|protected|Takie samo znaczenie jak standardu C++ w obrębie aplikacji lub składnika i w metadanych.|Tak|  
|public|Takie samo znaczenie jak standardu C++.|Tak|  
|`public protected` - lub - `protected public`|Chronione ułatwień dostępu w metadanych publicznych w ramach aplikacji lub składnika.|Tak|  
|`protected private` lub `private protected`|Nie są widoczne w metadanych; chronione ułatwień dostępu w aplikacji lub składnika.||  
|`internal` lub `private public`|Element członkowski nie jest publiczny w aplikacji lub składnik, ale nie jest widoczny w metadanych.|Nie|  
  
## <a name="windows-runtime-namespaces"></a>Przestrzenie nazw środowiska wykonawczego systemu Windows  
 Interfejs API systemu Windows, który składa się z typów, które są zadeklarowane w oknach::\* przestrzeni nazw. Te obszary nazw są zarezerwowane dla systemu Windows i typów nie można dodać do nich. W **przeglądarki obiektów**, można wyświetlić te przestrzenie nazw w pliku plik windows.winmd. Dokumentacja tych obszarów nazw, zobacz [interfejsu API systemu Windows](http://msdn.microsoft.com/library/windows/apps/br211377).  
  
## <a name="ccx-namespaces"></a>C + +/ CX przestrzenie nazw  
 C + +/ CX Definiowanie niektórych typów w tych obszarach nazw jako część projekcji system typów środowiska wykonawczego systemu Windows.  
  
|||  
|-|-|  
|**Namespace**|**Opis**|  
|default|Zawiera wbudowane typy numeryczne i char16. Te typy są w zakresie w każdej przestrzeni nazw i `using` instrukcji nigdy nie jest wymagana.|  
|Platforma|Zawiera typy głównie publiczne, które odpowiadają typów środowiska wykonawczego systemu Windows, takich jak `Array<T>`, `String`, `Guid`, i `Boolean`. Zawiera także typy specjalne pomocnika, takich jak `Platform::Agile<T>` i `Platform::Box<T>`.|  
|Platform::Collections|Zawiera klasy konkretnych kolekcji, które implementują interfejsy kolekcji środowiska wykonawczego systemu Windows `IVector`, `IMap`i tak dalej. Te typy są zdefiniowane w pliku nagłówka, collection.h nie znajduje się w platform.winmd.|  
|Platform::details|Zawiera typy, które są używane przez kompilator i nie są przeznaczone dla publicznych zużycia.|  
  
## <a name="see-also"></a>Zobacz też  
 [System typów (C++/CX)](../cppcx/type-system-c-cx.md)