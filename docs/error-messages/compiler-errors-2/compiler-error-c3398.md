---
title: Błąd kompilatora C3398 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 336494ea9581289efd9a41e604a28984125ae61a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018135"
---
# <a name="compiler-error-c3398"></a>Błąd kompilatora C3398

'operator': nie można konwertować z "function_signature" do "function_pointer". Wyrażenie źródłowe musi być symbolem funkcji

Gdy [__clrcall](../../cpp/clrcall.md) konwencji wywoływania nie zostanie określony podczas kompilowania za pomocą **/CLR**, kompilator generuje dwa punkty wejścia (adresów) dla każdej funkcji, natywnego punktu wejścia i zarządzany punkt wejścia.

Domyślnie kompilator powraca natywnego punktu wejścia, ale istnieją przypadki, gdzie pożądana jest zarządzany punkt wejścia (na przykład podczas przypisywania adresu `__clrcall` — wskaźnik funkcji). Aby kompilator niezawodnie wybierz zarządzany punkt wejścia w przypisania po prawej stronie musi być symbolem funkcji.