---
title: Kompilator ostrzeżenie (poziom 1) C4799 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3d83917289e5ad76a874587894a66e163fed90a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088231"
---
# <a name="compiler-warning-level-1-c4799"></a>Kompilator ostrzeżenie (poziom 1) C4799

> Nie EMMS na końcu funkcji "*funkcja*"

Funkcja ma co najmniej jednej instrukcji MMX, ale nie ma `EMMS` instrukcji. Użycie instrukcji multimedialnych `EMMS` instrukcji lub `_mm_empty` wewnętrzne należy również wyczyścić word multimedialnych znacznik na końcu kod MMX.

C4799 może wystąpić, gdy za pomocą ivec.h, wskazującą, czy kod nie korzysta z prawidłowo wykonania instrukcji EMMS przed zwróceniem. Jest to fałszywe ostrzeżenie dla tych nagłówków. Licencjobiorca może wyłączyć te definiując _SILENCE_IVEC_C4799 w ivec.h. Należy jednak pamiętać, że także zapobiegnie kompilator od wydawania poprawne ostrzeżenia tego typu.

Aby uzyskać powiązane informacje, zobacz [firmy Intel MMX rozkazów](../../assembler/inline/intel-s-mmx-instruction-set.md).