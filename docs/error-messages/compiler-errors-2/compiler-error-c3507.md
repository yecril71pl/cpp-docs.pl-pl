---
title: Błąd kompilatora C3507
ms.date: 11/04/2016
f1_keywords:
- C3507
helpviewer_keywords:
- C3507
ms.assetid: 75f89767-f6f9-40f6-9820-81a49e09abdf
ms.openlocfilehash: 731e84955192688a87c020b2b65a80ab5671cad6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363937"
---
# <a name="compiler-error-c3507"></a>Błąd kompilatora C3507

Identyfikator ProgID może zawierać nie więcej niż 39 znaków 'id'; nie zawierać żadnych znaków interpunkcyjnych z wyjątkiem '.'; ani rozpoczynających się od cyfry

[Progid](../../windows/progid.md) atrybut ma ograniczenia na podstawie wartości, które można wykonać.

Poniższy przykład spowoduje wygenerowanie C3507:

```
// C3507.cpp
[module(name="x")];
[
coclass,
progid("0123456789012345678901234567890123456789"),
uuid("00000000-0000-0000-0000-000000000001") // C3507 expected
]
struct CMyStruct {
};
int main() {
}
```