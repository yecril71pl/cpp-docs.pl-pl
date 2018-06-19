---
title: C3398 błąd kompilatora | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b870479977bfb49ff39d5a15fe19fc700ed66b8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255834"
---
# <a name="compiler-error-c3398"></a>C3398 błąd kompilatora
"operator": nie można przekonwertować z "function_signature" na "function_pointer". Wyrażenie źródłowe musi być symbolem funkcji  
  
 Gdy [__clrcall](../../cpp/clrcall.md) konwencji wywoływania nie zostanie określony podczas kompilowania za pomocą **/CLR**, kompilator generuje dwa punkty wejścia (adresy) dla każdej funkcji, punkt wejścia macierzystego i zarządzany punkt wejścia.  
  
 Domyślnie kompilator zwraca punkt wejścia natywnej, ale istnieją przypadki, gdy wymagane jest zarządzany punkt wejścia (na przykład podczas przypisywania adresu `__clrcall` wskaźnik funkcji). Kompilator niezawodnie wybierz zarządzany punkt wejścia w przypisaniu, po prawej stronie musi być symbolem funkcji.