---
title: "Auto — słowo kluczowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: auto_cpp
dev_langs: C++
helpviewer_keywords:
- automatic storage class [C++], auto keyword
- auto keyword [C++]
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 21b2155ffd5bb3861202c112bd9552ed36113a02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="auto-keyword"></a>auto — słowo kluczowe
`auto` — Słowo kluczowe jest Specyfikator deklaracji. Jednak C++ standard definiuje oryginalny i poprawione znaczenie dla tego słowa kluczowego. Przed Visual C++ 2010 `auto` — słowo kluczowe deklaruje zmienną w *automatyczne* Klasa magazynu; oznacza to, że zmienna, która ma lokalnego czas istnienia. Począwszy od programu Visual C++ 2010, `auto` — słowo kluczowe deklaruje zmienną, którego typ jest ustalane z wyrażenia inicjowania w jego deklaracji. [/Zc: Auto &#91;-&#93;](../build/reference/zc-auto-deduce-variable-type.md) — opcja kompilatora steruje znaczenie `auto` — słowo kluczowe.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>Uwagi  
 Definicja `auto` zmiany słów kluczowych w języku programowania C++, ale nie w języku programowania C.  
  
 W poniższych tematach opisano `auto` — słowo kluczowe i odpowiedniej opcji kompilatora:  
  
-   [automatycznie](../cpp/auto-cpp.md) opisano nową definicję `auto` — słowo kluczowe.  
  
  
-   [/ Zc: Auto (dedukuj typ zmiennej)](../build/reference/zc-auto-deduce-variable-type.md) opisuje opcję kompilatora, która informuje kompilator, która definicja `auto` — słowo kluczowe do użycia.  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)