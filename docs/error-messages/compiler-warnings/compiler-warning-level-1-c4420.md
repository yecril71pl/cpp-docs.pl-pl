---
title: Kompilator ostrzeżenie (poziom 1) C4420 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4420
dev_langs:
- C++
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1ba4ef4c4fc006e1a5950d0d16dc530ccc06a1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049751"
---
# <a name="compiler-warning-level-1-c4420"></a>Kompilator ostrzeżenie (poziom 1) C4420

'operator': operator nie jest dostępny, zamiast 'operator'; Sprawdzanie środowiska wykonawczego mogą być narażone na ataki

To ostrzeżenie jest generowane, gdy używasz [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector sprawdzania nowych elementów i usuwania) i gdy znajduje się żadna z form wektora. W tym przypadku jest używany formularz-wektor.

Aby /RTCv działała prawidłowo, kompilator zawsze powinna wywołać formie wektor [nowe](../../cpp/new-operator-cpp.md)/[Usuń](../../cpp/delete-operator-cpp.md) Jeśli użyto składni wektora.