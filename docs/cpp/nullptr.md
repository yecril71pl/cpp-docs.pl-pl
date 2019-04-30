---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 57be8d71f1dac4f347ea6567c02a385719bb7306
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403493"
---
# <a name="nullptr"></a>nullptr

Określa stałą pustego wskaźnika typu `std::nullptr_t`, który jest konwertowany na dowolny typ surowy wskaźnik.  Chociaż można używać słowa kluczowego **nullptr** bez uwzględniania żadnych nagłówków, jeśli kod używa typu `std::nullptr_t`, a następnie zdefiniuj, łącznie z nagłówkiem `<cstddef>`.

> [!NOTE]
>  **Nullptr** — słowo kluczowe również jest zdefiniowany w C++/interfejs wiersza polecenia dla aplikacje kodu zarządzanego i nie jest standardem ISO C++ — słowo kluczowe. Jeśli Twój kod może być skompilowany przy użyciu [/CLR](../build/reference/clr-common-language-runtime-compilation.md) następnie użyć opcji kompilatora, która jest przeznaczony dla kodu zarządzanego, `__nullptr` w każdym wierszu kodu, gdzie musisz gwarantować, że kompilator używa natywnego interpretacji języka C++. Aby uzyskać więcej informacji, zobacz [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Uwagi

Należy unikać wartość NULL lub wartość zero (`0`) jako stała wskaźnika o wartości null; **nullptr** mniej podatne na nadużycie i sprawdzi się najlepiej w większości sytuacji.  Na przykład, biorąc pod uwagę `func(std::pair<const char *, double>)`, następnie wywoływania `func(std::make_pair(NULL, 3.14))` powoduje błąd kompilatora.  Makro rozszerza się o wartości NULL, aby `0`, tak aby wywołanie `std::make_pair(0, 3.14)` zwraca `std::pair<int, double>`, który nie jest możliwa do przekonwertowania na (func) `std::pair<const char *, double>` typ parametru.  Wywoływanie `func(std::make_pair(nullptr, 3.14))` kompiluje pomyślnie, ponieważ `std::make_pair(nullptr, 3.14)` zwraca `std::pair<std::nullptr_t, double>`, który jest konwertowany na `std::pair<const char *, double>`.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++sposób niezamierzony)