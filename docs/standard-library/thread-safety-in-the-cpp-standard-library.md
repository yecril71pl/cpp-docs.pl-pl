---
title: Bezpieczeństwo wątku w standardowej bibliotece C++
ms.date: 11/04/2016
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
ms.openlocfilehash: 4ac029a119a77fa87c6cd004fece9c4e6b382026
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460064"
---
# <a name="thread-safety-in-the-c-standard-library"></a>Bezpieczeństwo wątku w standardowej bibliotece C++

Następujące reguły zabezpieczeń wątku mają zastosowanie do wszystkich klas w bibliotece C++ standardowej — w tym `shared_ptr`, jak opisano poniżej.  Są czasami dostępne silniejsze gwarancje — na przykład standardowe obiekty iostream, jak opisano poniżej, i typy przeznaczone dla wielowątkowości, takie jak te w [ \<>](../standard-library/atomic.md)niepodzielnych.

Obiekt jest bezpieczny wątkowo do odczytu z wielu wątków. Na przykład, mając obiekt A, można bezpiecznie odczytać z wątku 1 i z wątku 2 jednocześnie.

Jeśli obiekt jest zapisywany do jednego wątku, wszystkie operacje odczytu i zapisu do tego obiektu w tym samym lub innych wątkach muszą być chronione. Na przykład, mając obiekt A, jeśli wątek 1 jest zapisywany w, wówczas wątek 2 musi być zablokowany do odczytu lub zapisu w.

Można bezpiecznie odczytywać i zapisywać dane w jednym wystąpieniu typu, nawet jeśli inny wątek odczytuje lub zapisuje w innym wystąpieniu tego samego typu. Na przykład obiekty A i B tego samego typu są bezpieczne, gdy jest zapisywany w wątku 1 i B jest odczytywany w wątku 2.

## <a name="sharedptr"></a>shared_ptr

Wiele wątków może jednocześnie odczytywać i zapisywać różne obiekty [shared_ptr](../standard-library/shared-ptr-class.md) , nawet gdy obiekty są kopiowane, które współdzielą własność.

## <a name="iostream"></a>iostream

Standardowe `cin`obiekty iostream ,`wcin` ,,`wclog` ,, i są zgodne z tymi samymi regułami co inne klasy, z wyjątkiem tego wyjątku: jest to bezpieczne `cout` `cerr` `clog` `wcout` `wcerr` Zapisz w obiekcie z wielu wątków. Na przykład wątek 1 może zapisywać do [cout](../standard-library/iostream.md#cout) w tym samym czasie co wątek 2. Jednak może to spowodować, że dane wyjściowe z dwóch wątków mają być mieszane.

> [!NOTE]
> Odczyt z buforu strumienia nie jest uważany za operację odczytu. Zamiast tego uznaje się, że jest to operacja zapisu, ponieważ stan klasy jest zmieniany.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)
