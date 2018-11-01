---
title: Kompilator ostrzeżenie (poziom 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: a4a7e91e7845cc0fc25d5a6fad16ae7b7e327952
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662894"
---
# <a name="compiler-warning-level-1-c4420"></a>Kompilator ostrzeżenie (poziom 1) C4420

'operator': operator nie jest dostępny, zamiast 'operator'; Sprawdzanie środowiska wykonawczego mogą być narażone na ataki

To ostrzeżenie jest generowane, gdy używasz [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector sprawdzania nowych elementów i usuwania) i gdy znajduje się żadna z form wektora. W tym przypadku jest używany formularz-wektor.

Aby /RTCv działała prawidłowo, kompilator zawsze powinna wywołać formie wektor [nowe](../../cpp/new-operator-cpp.md)/[Usuń](../../cpp/delete-operator-cpp.md) Jeśli użyto składni wektora.