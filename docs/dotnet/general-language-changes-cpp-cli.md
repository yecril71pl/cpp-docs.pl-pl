---
title: Ogólne zmiany w języku (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b48ebdf0bf25399b08f8a1cb1240a857cfad352
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418466"
---
# <a name="general-language-changes-ccli"></a>Ogólne zmiany w języku (C++/CLI)

Liczba funkcji języka środowiska CLR zmieniła się z zarządzanych rozszerzeń dla C++ do Visual C++.

Zmiany opisane w tej sekcji są sortowania miscellany języka. Obejmuje zmiany w obsłudze literałów ciągu zmiany w przeciążeniu rozdzielczości między wielokropek i `Param` atrybutu zmiana `typeof` do `typeid`, zmiana wywołania listy inicjatorów konstruktora i wprowadzenie nowej notacji rzutowania z `safe_cast`.

[Literał ciągu](../dotnet/string-literal.md)<br/>
W tym artykule omówiono, jak zmiany obsługi literałów ciągu.

[Tablica parametrów i wielokropek](../dotnet/param-array-and-ellipsis.md)<br/>
W tym artykule omówiono sposób `ParamArray` jest teraz pierwszeństwo wielokropek (`...`) postępowania po otrzymaniu wywołania funkcji z różną liczbę argumentów.

[Operator typeof został zastąpiony operatorem T::typeid](../dotnet/typeof-goes-to-t-typeid.md)<br/>
W tym artykule omówiono sposób, w jaki `typeof` operator ma zostać supplanted przez `typeid`.

[Listy inicjatorów](../dotnet/initializer-lists.md)<br/>
W tym artykule omówiono zmiany w kolejności wywołań list inicjatorów.

[Notacja rzutowania i przedstawienie operacji safe_cast<>](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)<br/>
W tym artykule omówiono zmiany do notacji rzutowania, a w szczególności wprowadzenie `safe_cast`.

## <a name="see-also"></a>Zobacz też

[Podręcznik migracji C++/CLI](../dotnet/cpp-cli-migration-primer.md)