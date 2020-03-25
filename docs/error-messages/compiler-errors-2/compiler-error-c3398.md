---
title: Błąd kompilatora C3398
ms.date: 11/04/2016
f1_keywords:
- C3398
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
ms.openlocfilehash: f76515d58f020b414e6b79a7737463af80bd2d07
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200822"
---
# <a name="compiler-error-c3398"></a>Błąd kompilatora C3398

"operator": nie można konwertować z "function_signature" na "function_pointer". Wyrażenie źródłowe musi być symbolem funkcji

Gdy nie określono konwencji wywoływania [__clrcall](../../cpp/clrcall.md) podczas kompilowania z **/CLR**, kompilator generuje dwa punkty wejścia (addresss) dla każdej funkcji, natywnego punktu wejścia i zarządzanego punktu wejścia.

Domyślnie kompilator zwraca natywny punkt wejścia, ale istnieją sytuacje, w których jest wymagany zarządzany punkt wejścia (na przykład podczas przypisywania adresu do wskaźnika funkcji `__clrcall`). Aby kompilator mógł niezawodnie wybrać zarządzany punkt wejścia w przypisaniu, po prawej stronie musi być symbolem funkcji.
