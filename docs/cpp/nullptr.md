---
title: nullptr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- nullptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07e05e3a1c1b25e87053e15244f3c5fb9db442d9
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404164"
---
# <a name="nullptr"></a>nullptr
Określa stałą pustego wskaźnika typu `std::nullptr_t`, który jest konwertowany na dowolny typ surowy wskaźnik.  Chociaż można używać słowa kluczowego **nullptr** bez uwzględniania żadnych nagłówków, jeśli kod używa typu `std::nullptr_t`, a następnie zdefiniuj, łącznie z nagłówkiem `<cstddef>`.  
  
> [!NOTE]
>  **Nullptr** — słowo kluczowe również jest zdefiniowany w języku C + +/ interfejsu wiersza polecenia dla aplikacje kodu zarządzanego i nie jest słowem kluczowym ISO Standard C++. Jeśli Twój kod może być skompilowany przy użyciu [/CLR](../build/reference/clr-common-language-runtime-compilation.md) następnie użyć opcji kompilatora, która jest przeznaczony dla kodu zarządzanego, `__nullptr` w każdym wierszu kodu, gdzie musisz gwarantować, że kompilator używa natywnego interpretacji języka C++. Aby uzyskać więcej informacji, zobacz [nullptr](../windows/nullptr-cpp-component-extensions.md).  
  
## <a name="remarks"></a>Uwagi  
 Należy unikać wartość NULL lub wartość zero (`0`) jako stała wskaźnika o wartości null; **nullptr** mniej podatne na nadużycie i sprawdzi się najlepiej w większości sytuacji.  Na przykład, biorąc pod uwagę `func(std::pair<const char *, double>)`, następnie wywoływania `func(std::make_pair(NULL, 3.14))` powoduje błąd kompilatora.  Makro rozszerza się o wartości NULL, aby `0`, tak aby wywołanie `std::make_pair(0, 3.14)` zwraca `std::pair<int, double>`, który nie jest możliwa do przekonwertowania na (func) `std::pair<const char *, double>` typ parametru.  Wywoływanie `func(std::make_pair(nullptr, 3.14))` kompiluje pomyślnie, ponieważ `std::make_pair(nullptr, 3.14)` zwraca `std::pair<std::nullptr_t, double>`, który jest konwertowany na `std::pair<const char *, double>`.  
  
## <a name="see-also"></a>Zobacz także  
 [Keywords](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)