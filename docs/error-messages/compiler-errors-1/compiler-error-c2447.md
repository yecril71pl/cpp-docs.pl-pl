---
title: Błąd kompilatora C2447
ms.date: 11/04/2016
f1_keywords:
- C2447
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
ms.openlocfilehash: 14fec374927fc798956a249773d9bec814e7a823
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744189"
---
# <a name="compiler-error-c2447"></a>Błąd kompilatora C2447

'{': brak nagłówka funkcji (stary styl listy formalnej)?

Kompilator napotkał nieoczekiwany otwierający nawias klamrowy w zakresie globalnym. W większości przypadków jest to spowodowane przez nieprawidłowo sformułowany nagłówek funkcji, deklarację umieszczoną w złym miejscu lub zabłąkany średnik. Aby rozwiązać ten problem, sprawdź, czy otwierający nawias klamrowy następuje po poprawnie sformułowanym nagłówku funkcji i nie jest poprzedzony przez deklarację lub zabłąkany średnik.

Ten błąd może być też spowodowany listą argumentów formalnych języka C w starym stylu. Aby rozwiązać ten problem, zreorganizuj listę argumentów, aby używała stylu nowoczesnego — to znaczy ujętego w nawiasy.

Poniższy przykład generuje C2447:

```cpp
// C2447.cpp
int c;
{}       // C2447
```
