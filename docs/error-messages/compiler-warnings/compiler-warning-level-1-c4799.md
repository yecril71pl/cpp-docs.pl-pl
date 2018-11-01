---
title: Kompilator ostrzeżenie (poziom 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: 475451b47d461e7ea1428eb715a876fb023694d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552259"
---
# <a name="compiler-warning-level-1-c4799"></a>Kompilator ostrzeżenie (poziom 1) C4799

> Nie EMMS na końcu funkcji "*funkcja*"

Funkcja ma co najmniej jednej instrukcji MMX, ale nie ma `EMMS` instrukcji. Użycie instrukcji multimedialnych `EMMS` instrukcji lub `_mm_empty` wewnętrzne należy również wyczyścić word multimedialnych znacznik na końcu kod MMX.

C4799 może wystąpić, gdy za pomocą ivec.h, wskazującą, czy kod nie korzysta z prawidłowo wykonania instrukcji EMMS przed zwróceniem. Jest to fałszywe ostrzeżenie dla tych nagłówków. Licencjobiorca może wyłączyć te definiując _SILENCE_IVEC_C4799 w ivec.h. Należy jednak pamiętać, że także zapobiegnie kompilator od wydawania poprawne ostrzeżenia tego typu.

Aby uzyskać powiązane informacje, zobacz [firmy Intel MMX rozkazów](../../assembler/inline/intel-s-mmx-instruction-set.md).