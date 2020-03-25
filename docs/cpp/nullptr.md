---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 223f4c3e8c838698f9716e241543db405c9394af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177771"
---
# <a name="nullptr"></a>nullptr

Wyznacza stałą wskaźnika o wartości null typu `std::nullptr_t`, która jest możliwa do przekonwertowania na dowolny nieprzetworzony typ wskaźnika.  Chociaż można użyć słowa kluczowego **nullptr** bez dołączania żadnych nagłówków, jeśli kod używa typu `std::nullptr_t`, należy go zdefiniować przez dołączenie nagłówka `<cstddef>`.

> [!NOTE]
>  Słowo kluczowe **nullptr** jest również zdefiniowane w C++/CLI dla aplikacji kodu zarządzanego i nie jest zamienne ze standardowym C++ słowem kluczowym ISO. Jeśli kod można skompilować przy użyciu opcji kompilatora [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , która kieruje kod zarządzany, a następnie użyj `__nullptr` w dowolnym wierszu kodu, w którym należy zagwarantować, że kompilator używa natywnej C++ interpretacji. Aby uzyskać więcej informacji, zobacz [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Uwagi

Należy unikać używania wartości NULL lub zero (`0`) jako stałej wskaźnika o wartości null; **nullptr** jest mniej podatny na niewłaściwe użycie i działa lepiej w większości sytuacji.  Na przykład, dana `func(std::pair<const char *, double>)`, wywołanie `func(std::make_pair(NULL, 3.14))` powoduje błąd kompilatora.  Makro jest rozwijane do `0`, dzięki czemu wywołanie `std::make_pair(0, 3.14)` zwraca `std::pair<int, double>`, które nie jest konwertowane na typ parametru `std::pair<const char *, double>` typu Func ().  Wywoływanie `func(std::make_pair(nullptr, 3.14))` zostało pomyślnie skompilowane, ponieważ `std::make_pair(nullptr, 3.14)` zwraca `std::pair<std::nullptr_t, double>`, który jest konwertowany na `std::pair<const char *, double>`.

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)
