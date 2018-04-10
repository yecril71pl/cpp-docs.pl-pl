---
title: nullptr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- nullptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3063a93361095a9d51152ce93f8522365513cf67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="nullptr"></a>nullptr
Określa stałą pustego wskaźnika typu `std::nullptr_t`, która jest możliwe do przekonwertowania na dowolny typ wskaźnika raw.  Mimo że można użyć słowa kluczowego `nullptr` bez uwzględniania wszelkie nagłówki, jeśli kod używa typu `std::nullptr_t`, a następnie zdefiniuj przez dołączenie nagłówka `<cstddef>`.  
  
> [!NOTE]
>  `nullptr` — Słowo kluczowe jest też definiowany w języku C + +/ CLI dla aplikacje kodu zarządzanego i nie jest wymienne ze słowem kluczowym ISO Standard C++. Jeśli kod może być kompilowana przy użyciu [/CLR](../build/reference/clr-common-language-runtime-compilation.md) następnie użyć opcji kompilatora, która jest przeznaczony dla kodu zarządzanego, `__nullptr` w każdym wierszu kodu, gdzie należy zagwarantować, że kompilator używa natywnego interpretacji języka C++. Aby uzyskać więcej informacji, zobacz [nullptr](../windows/nullptr-cpp-component-extensions.md).  
  
## <a name="remarks"></a>Uwagi  
 Unikaj używania `NULL` lub wartość zero (`0`) jako stałą pustego wskaźnika; `nullptr` mniej podatne na nieprawidłowe użycie i działa lepiej w większości sytuacji.  Na przykład `func(std::pair<const char *, double>)`, wywołując `func(std::make_pair(NULL, 3.14))` powoduje błąd kompilatora.  Makro NULL rozwijany do `0`, dzięki czemu wywołanie `std::make_pair(0, 3.14)` zwraca `std::pair<int, double>`, która nie jest możliwe do przekonwertowania na (func) `std::pair<const char *, double>` typ parametru.  Wywoływanie `func(std::make_pair(nullptr, 3.14))` pomyślnie kompiluje ponieważ `std::make_pair(nullptr, 3.14)` zwraca `std::pair<std::nullptr_t, double>`, która jest możliwe do przekonwertowania na `std::pair<const char *, double>`.  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)