---
title: Kompilator ostrzeżenie (poziom 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: 99f4f45aad82aa9898dad4cffb60b8e3311ddc9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152146"
---
# <a name="compiler-warning-level-1-c4042"></a>Kompilator ostrzeżenie (poziom 1) C4042

'Identyfikator': ma złą klasę magazynu

Klasa wybrany magazyn nie można używać z tego identyfikatora w tym kontekście. Kompilator używa domyślnej klasy magazynu, zamiast tego:

- `extern`, jeśli *identyfikator* jest funkcją.

- **automatyczne**, jeśli *identyfikator* formalny parametr lub zmienna lokalna.

- Brak magazynu klasy, jeśli *identyfikator* jest zmienną globalną.

To ostrzeżenie może być spowodowany przez określenie klasę magazynu innego niż **zarejestrować** w deklaracji parametru.

Poniższy przykład spowoduje wygenerowanie C4042

```
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```