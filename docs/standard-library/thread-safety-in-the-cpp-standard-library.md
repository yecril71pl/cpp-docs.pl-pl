---
title: Bezpieczeństwo wątku w standardowej bibliotece C++
ms.date: 11/04/2016
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
ms.openlocfilehash: 27ac930e567521b12dfc35e2f8c4c389c35ae47d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607639"
---
# <a name="thread-safety-in-the-c-standard-library"></a>Bezpieczeństwo wątku w standardowej bibliotece C++

Następujące zasady bezpieczeństwa wątku zastosowanie do wszystkich klas w standardowej biblioteki języka C++ — dotyczy to również `shared_ptr`, zgodnie z poniższym opisem.  Czasami znajdują się lepsze gwarancje — na przykład standardowy iostream obiekty, zgodnie z poniższym opisem i typy przeznaczony specjalnie dla wielowątkowości, takich jak te w [ \<atomic >](../standard-library/atomic.md).

Obiekt jest bezpieczna dla wątków do odczytu z wielu wątków. Na przykład biorąc pod uwagę obiekt A, jest bezpieczne, A z wątku 1 i 2 wątków jednocześnie odczytać.

Jeśli obiekt jest zapisywany w jednego wątku, następnie wszystkich operacji odczytu i zapisu do tego obiektu w tym samym lub inne wątki, które muszą być chronione. Na przykład biorąc pod uwagę obiekt A, jeśli wątek 1 zapisuje element, następnie wątek 2 należy uniemożliwić odczytu / zapisu do serwera A.

Jest bezpieczne do odczytu i zapisu do pojedynczego wystąpienia typu, nawet jeśli inny wątek jest odczyt lub zapis do innego wystąpienia tego samego typu. Na przykład biorąc pod uwagę obiektów, A i B tego samego typu, jest bezpieczne podczas zapisywany w wątku 1 A i B jest odczytywany w wątku 2.

## <a name="sharedptr"></a>shared_ptr

Wiele wątków jednocześnie może odczytywać i zapisywać różne [shared_ptr](../standard-library/shared-ptr-class.md) obiektów, nawet wtedy, gdy obiekty są kopiami, które dzielą prawo własności.

## <a name="iostream"></a>iostream

Obiekty standardowa iostream `cin`, `cout`, `cerr`, `clog`, `wcin`, `wcout`, `wcerr`, i `wclog` wykonaj te same reguły jako inne klasy, z tym wyjątkiem: jest bezpieczne Napisz do obiektu z wielu wątków. Na przykład, można zapisać wątku 1 [cout](../standard-library/iostream.md#cout) w tym samym czasie jako wątek 2. Jednak może to spowodować dane wyjściowe z dwoma wątkami na się zmieszać.

> [!NOTE]
> Odczyt z buforu strumienia nie jest uważane za operacje odczytu. Zamiast tego jest on uznawany za być operacji zapisu, ponieważ stan klasy zmienił się.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
