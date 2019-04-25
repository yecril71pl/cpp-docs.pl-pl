---
title: Błąd kompilatora C3398
ms.date: 11/04/2016
f1_keywords:
- C3398
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
ms.openlocfilehash: 3b688012009a87c1e3d0db05e47133893daeaf34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300456"
---
# <a name="compiler-error-c3398"></a>Błąd kompilatora C3398

'operator': nie można konwertować z "function_signature" do "function_pointer". Wyrażenie źródłowe musi być symbolem funkcji

Gdy [__clrcall](../../cpp/clrcall.md) konwencji wywoływania nie zostanie określony podczas kompilowania za pomocą **/CLR**, kompilator generuje dwa punkty wejścia (adresów) dla każdej funkcji, natywnego punktu wejścia i zarządzany punkt wejścia.

Domyślnie kompilator powraca natywnego punktu wejścia, ale istnieją przypadki, gdzie pożądana jest zarządzany punkt wejścia (na przykład podczas przypisywania adresu `__clrcall` — wskaźnik funkcji). Aby kompilator niezawodnie wybierz zarządzany punkt wejścia w przypisania po prawej stronie musi być symbolem funkcji.