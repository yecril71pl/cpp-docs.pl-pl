---
title: Arytmetyczny wskaźnik
ms.date: 11/04/2016
helpviewer_keywords:
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
ms.openlocfilehash: 7ed238bdeedf95bb79543a28ed8dd602020fa55b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615478"
---
# <a name="pointer-arithmetic"></a>Arytmetyczny wskaźnik

Operacje dodawania, obejmująca wskaźnika i liczbą całkowitą zapewniają znaczących wyników, tylko wtedy, gdy argument wskaźnika adresów elementu członkowskiego tablicy, a wartość całkowitą spowoduje przesunięcie w granicach tej samej tablicy. Gdy Przesunięcie adresu jest konwertowany na wartość całkowitą, kompilator zakłada, że tylko pamięci stanowisk taki sam rozmiar mieszczą się pomiędzy oryginalnego adresu i adres oraz przesunięcie.

To założenie jest prawidłowy dla elementów tablicy. Zgodnie z definicją tablica jest szereg wartości tego samego typu; jego elementy znajdują się w lokalizacji pamięci ciągłej. Magazyn dla wszystkich typów, z wyjątkiem elementów tablicy nie jest gwarantowane do wypełnienia przez ten sam typ identyfikatorów. Oznacza to puste mogą występować między pozycjami pamięci, a nawet pozycji tego samego typu. W związku z tym wyniki dodawanie do lub odjęcie od adresów wartości, ale elementy tablicy są niezdefiniowane.

Podobnie gdy dwie wartości wskaźnika są odejmowane, konwersja przyjęto założenie, że tylko wartości tego samego typu, za pomocą niepustych, mieszczą się pomiędzy adresy podane przez argumenty operacji.

## <a name="see-also"></a>Zobacz też

[Operatory dodawania języka C](../c-language/c-additive-operators.md)