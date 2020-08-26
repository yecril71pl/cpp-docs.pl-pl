---
title: Przestrzenie nazw i widoczność typów (C++/CX)
ms.date: 12/30/2016
ms.assetid: cbc01a3a-3b69-4ded-9c42-ecbf0fd0a00e
ms.openlocfilehash: 78d5f5af761cef985ec43cf448251b4dc3c70bc2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837804"
---
# <a name="namespaces-and-type-visibility-ccx-"></a>Przestrzenie nazw i widoczność typów (C++/CX)

Przestrzeń nazw to standardowa konstrukcja języka C++ dla typów grupowania, które mają powiązane funkcje i zapobiegania kolizjom nazw w bibliotekach. System środowisko wykonawcze systemu Windows Type wymaga, aby wszystkie typy publiczne środowisko wykonawcze systemu Windows, łącznie z tymi w własnym kodzie, muszą być zadeklarowane w przestrzeni nazw w zakresie przestrzeni nazw. Typy publiczne, które są zadeklarowane w zakresie globalnym lub zagnieżdżone w innej klasie, spowodują błąd czasu kompilacji.

Plik. winmd musi mieć taką samą nazwę, która ma główną przestrzeń nazw. Na przykład Klasa o nazwie A. B. C. MyClass można utworzyć wystąpienie tylko wtedy, gdy jest zdefiniowana w pliku metadanych o nazwie A. winmd lub A. B. winmd lub A. B. winmd. Nazwa pliku wykonywalnego nie jest wymagana w celu dopasowania do jego nazwy.

## <a name="type-visibility"></a>Widoczność typu

W przestrzeni nazw środowisko wykonawcze systemu Windows typy — w przeciwieństwie do standardowych typów C++ — mają dostępność prywatną lub publiczną. Domyślnie dostępność jest prywatna. Tylko typ publiczny jest widoczny dla metadanych i dlatego jest zużywany z aplikacji i składników, które mogą być zapisywane w językach innych niż C++. Ogólnie rzecz biorąc, reguły dla widocznych typów są bardziej restrykcyjne niż reguły dla niewidocznych typów, ponieważ typy widoczne nie mogą uwidaczniać pojęć specyficznych dla języka C++, które nie są obsługiwane w językach .NET lub JavaScript.

> [!NOTE]
> Metadane są używane tylko w czasie wykonywania przez Języki .NET i JavaScript. Gdy aplikacja lub składnik języka C++ jest w trakcie rozmowy z inną aplikacją lub składnikiem C++ — obejmuje to składniki systemu Windows, które są zapisywane w języku C++ — nie jest wymagane użycie metadanych w czasie wykonywania.

## <a name="member-accessibility-and-visibility"></a>Dostępność i widoczność członków

W prywatnej klasie ref, interfejsie lub delegatze żadne elementy członkowskie nie są emitowane do metadanych, nawet jeśli mają publiczny dostęp. W publicznych klasach ref można kontrolować widoczność elementów członkowskich w metadanych niezależnie od ich dostępności w kodzie źródłowym. Podobnie jak w przypadku standardu C++, stosuj zasadę najniższych uprawnień; nie należy wprowadzać członków do metadanych, chyba że są one absolutnie konieczne.

Poniższe Modyfikatory dostępu umożliwiają kontrolowanie zarówno widoczności metadanych, jak i ułatwień dostępu do kodu źródłowego.

| Modyfikator | Znaczenie | Emituje do metadanych? |
|--|--|--|
| **`private`** | Domyślny dostęp. Takie samo znaczenie jak w przypadku standardowego języka C++. | Nie |
| **`protected`** | Takie samo, jak w przypadku standardowego języka C++, zarówno w ramach aplikacji, jak i składnika, jak i w metadanych. | Tak |
| **`public`** | Takie samo znaczenie jak w przypadku standardowego języka C++. | Tak |
| **`public protected`** oraz **`protected public`** | Chroniona dostępność w metadanych, publiczna w aplikacji lub składniku. | Tak |
| **`protected private`** oraz **`private protected`** | Niewidoczne w metadanych; chroniona dostępność w aplikacji lub składniku. |  |
| **`internal`** oraz **`private public`** | Element członkowski jest publiczny w aplikacji lub składniku, ale nie jest widoczny w metadanych. | Nie |

## <a name="windows-runtime-namespaces"></a>środowisko wykonawcze systemu Windows przestrzenie nazw

Interfejs API systemu Windows składa się z typów, które są zadeklarowane w \* przestrzeniach nazw Windows::. Te przestrzenie nazw są zastrzeżone dla systemu Windows i nie można do nich dodawać typów. W **Przeglądarka obiektów**można wyświetlić te przestrzenie nazw w pliku. winmd systemu Windows. Aby uzyskać dokumentację dotyczącą tych przestrzeni nazw, zobacz [Windows API](/uwp/api/).

## <a name="ccx-namespaces"></a>Przestrzenie nazw C++/CX

C++/CX definiują niektóre typy w tych przestrzeniach nazw jako część projekcji systemu typu środowisko wykonawcze systemu Windows.

| Przestrzeń nazw | Opis |
|--|--|
| default | Zawiera wbudowane typy liczbowe i char16. Te typy są w zakresie w każdej przestrzeni nazw, a **`using`** instrukcja nie jest nigdy wymagana. |
| `Platform` | Zawiera głównie typy publiczne, które odpowiadają typom środowisko wykonawcze systemu Windows `Array<T>` , takich jak,, `String` `Guid` i `Boolean` . Zawiera również wyspecjalizowane typy pomocnika, takie jak `Platform::Agile<T>` i `Platform::Box<T>` . |
| `Platform::Collections` | Zawiera klasy konkretnych kolekcji, które implementują interfejsy kolekcji środowisko wykonawcze systemu Windows `IVector` , `IMap` i tak dalej. Te typy są zdefiniowane w pliku nagłówkowym, Collection. h, a nie na platformie. winmd. |
| `Platform::Details` | Zawiera typy, które są używane przez kompilator i nie są przeznaczone do użycia publicznego. |

## <a name="see-also"></a>Zobacz też

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)
