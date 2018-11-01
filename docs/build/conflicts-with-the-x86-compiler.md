---
title: Konflikty z kompilatorem x86
ms.date: 11/04/2016
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
ms.openlocfilehash: e56ebc5631ac5c96a9cdd2dfc2b8e81cdeed9769
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614269"
---
# <a name="conflicts-with-the-x86-compiler"></a>Konflikty z kompilatorem x86

Typy danych, które są większe niż 4 bajty nie będą automatycznie wyrównywane do stosu w przypadku użycia x86 kompilatora do skompilowania aplikacji. Ponieważ architektury x86 kompilator jest stosu wyrównany 4-bajtowych, większe niż 4 bajty, na przykład 64-bitowa liczba całkowita, nie można automatycznie wyrównywane do adresu 8-bajtowych.

Praca z niewyrównanych danych ma dwa skutki.

- Może potrwać dłużej dostęp do niewyrównanych lokalizacji nie jest potrzebny dostęp do lokalizacji wyrównane.

- Niewyrównanych lokalizacji nie można używać w operacjach blokowane.

Jeśli potrzebujesz więcej wyrównanie strict, użyj `__declspec(align(N)) on your variable declarations`. To powoduje, że kompilator dynamicznie wyrównać stosu odpowiadających Twoim kryteriom. Dynamiczne Dostosowywanie stosu w czasie wykonywania mogą jednak spowodować wolniejszy wykonywanie aplikacji.

## <a name="see-also"></a>Zobacz też

[Typy i magazyn](../build/types-and-storage.md)<br/>
[align](../cpp/align-cpp.md)