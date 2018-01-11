---
title: "C3398 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3398
dev_langs: C++
helpviewer_keywords: C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4b332346dd8e8b7e906e961c86805ad0564f0f79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3398"></a>C3398 błąd kompilatora
"operator": nie można przekonwertować z "function_signature" na "function_pointer". Wyrażenie źródłowe musi być symbolem funkcji  
  
 Gdy [__clrcall](../../cpp/clrcall.md) konwencji wywoływania nie zostanie określony podczas kompilowania za pomocą **/CLR**, kompilator generuje dwa punkty wejścia (adresy) dla każdej funkcji, punkt wejścia macierzystego i zarządzany punkt wejścia.  
  
 Domyślnie kompilator zwraca punkt wejścia natywnej, ale istnieją przypadki, gdy wymagane jest zarządzany punkt wejścia (na przykład podczas przypisywania adresu `__clrcall` wskaźnik funkcji). Kompilator niezawodnie wybierz zarządzany punkt wejścia w przypisaniu, po prawej stronie musi być symbolem funkcji.