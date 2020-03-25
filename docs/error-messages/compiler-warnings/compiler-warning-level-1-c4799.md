---
title: Ostrzeżenie kompilatora (poziom 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: ec92da425718cd5ddc579d1d733a0bc4e56dc04a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175106"
---
# <a name="compiler-warning-level-1-c4799"></a>Ostrzeżenie kompilatora (poziom 1) C4799

> Brak EMMS na końcu funkcji "*Function*"

Funkcja ma co najmniej jedną instrukcję MMX, ale nie ma instrukcji `EMMS`. Gdy jest używana instrukcja multimedialna, `EMMS` instrukcji lub `_mm_empty` wewnętrznej należy również użyć, aby wyczyścić słowo tag multimedialny na końcu kodu MMX.

Użytkownik może uzyskać C4799 podczas korzystania z ivec. h, wskazując, że kod nie używa prawidłowo instrukcji EMMS przed zwróceniem. Jest to fałszywe ostrzeżenie dla tych nagłówków. Można je wyłączyć przez zdefiniowanie _SILENCE_IVEC_C4799 w IVEC. h. Należy jednak pamiętać, że spowoduje to również zachowanie przez kompilator prawidłowych ostrzeżeń tego typu.

Aby uzyskać powiązane informacje, zobacz [zestaw instrukcji MMX firmy Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).
