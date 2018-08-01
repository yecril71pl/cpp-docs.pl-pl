---
title: Auto — słowo kluczowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a02ed2a19f44f19396038f8e41cb1c7f5a069407
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405889"
---
# <a name="auto-keyword"></a>auto — słowo kluczowe
**Automatycznie** — słowo kluczowe jest Specyfikator deklaracji. Jednak C++ standard definiuje oryginału i poprawione znaczenie słowa kluczowego. Przed Visual C++ 2010 **automatycznie** — słowo kluczowe deklaruje zmienną w *automatyczne* klasę magazynu, czyli zmiennej, która ma lokalne okresy istnienia. Począwszy od programu Visual C++ 2010, **automatycznie** — słowo kluczowe deklaruje zmienną, którego typ jest ustalić na podstawie wyrażenia inicjowania w jego deklaracji. [/Zc: Auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md) — opcja kompilatora kontroluje znaczenie **automatycznie** — słowo kluczowe.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>Uwagi  
 Definicja **automatycznie** zmiany słów kluczowych w języku programowania C++, ale nie w języku programowania C.  
  
 W poniższych tematach opisano **automatycznie** — słowo kluczowe i odpowiadające opcje kompilatora:  
  
-   [automatyczne](../cpp/auto-cpp.md) opisuje nową definicję **automatycznie** — słowo kluczowe.  
  
-   [/ Zc: Auto (dedukuj typ zmiennej)](../build/reference/zc-auto-deduce-variable-type.md) opisuje opcję kompilatora, która informuje kompilator, która definicja **automatycznie** — słowo kluczowe do użycia.  
  
## <a name="see-also"></a>Zobacz także  
 [Słowa kluczowe](../cpp/keywords-cpp.md)