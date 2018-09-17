---
title: Powoduje konflikt z x86 kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f01e65adfb42a5fb3361e75ce34060f7dc1b9f9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709675"
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