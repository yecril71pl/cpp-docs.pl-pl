---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 51df20ea00e5dd77ab1fc1a2a01253b8f788ad0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358852"
---
# <a name="nullptr"></a>nullptr

Wyznacza stałą wskaźnika `std::nullptr_t`zerowego typu , która jest konwertowana na dowolny typ nieprzetworzonego wskaźnika.  Chociaż można użyć słowa kluczowego **nullptr** bez uwzględnienia żadnych nagłówków, jeśli kod używa typu, `std::nullptr_t`należy zdefiniować go, dołączając nagłówek `<cstddef>`.

> [!NOTE]
> **Nullptr** słowo kluczowe jest również zdefiniowane w języku C++/CLI dla aplikacji kodu zarządzanego i nie jest wymienne z ISO Standard C++ słowa kluczowego. Jeśli kod może być skompilowany przy użyciu [/clr](../build/reference/clr-common-language-runtime-compilation.md) kompilatora opcji, która jest przeznaczona dla kodu zarządzanego, a następnie użyć `__nullptr` w dowolnym wierszu kodu, gdzie należy zagwarantować, że kompilator używa natywnej interpretacji języka C++. Aby uzyskać więcej informacji, zobacz [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Uwagi

Należy unikać używania`0`NULL lub zero ( ) jako stałej wskaźnika zerowego; **nullptr** jest mniej podatny na nadużycia i działa lepiej w większości sytuacji.  Na przykład `func(std::pair<const char *, double>)`podane , `func(std::make_pair(NULL, 3.14))` a następnie wywołanie powoduje błąd kompilatora.  Wartość NULL makra `0`zostanie rozwinięta `std::make_pair(0, 3.14)` `std::pair<int, double>`do wartości , tak aby wywołanie `std::pair<const char *, double>` zwracał , które nie jest konwertowane na typ parametru func().  Wywołanie `func(std::make_pair(nullptr, 3.14))` pomyślnie `std::make_pair(nullptr, 3.14)` kompiluje, ponieważ zwraca `std::pair<std::nullptr_t, double>`, który jest konwertowany na `std::pair<const char *, double>`.

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)
