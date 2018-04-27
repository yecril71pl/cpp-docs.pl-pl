---
title: Bezpieczeństwo wątku w standardowej bibliotece C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bad79ad237e388167a747d6af662fff3d9d05497
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="thread-safety-in-the-c-standard-library"></a>Bezpieczeństwo wątku w standardowej bibliotece C++

Mają zastosowanie następujące reguły bezpieczeństwa wątków wszystkie klasy w standardowej bibliotece C++ — dotyczy to również `shared_ptr`, zgodnie z poniższym opisem.  Czasami podano większą — na przykład standardowe iostream obiekty, zgodnie z poniższym opisem i typy przeznaczony specjalnie dla wielowątkowości, jak w [ \<atomic >](../standard-library/atomic.md).

Obiekt jest bezpieczne wątkowo odczytu z wielu wątków. Na przykład mając obiektu A, jest bezpieczne odczytać A z wątku 1 i 2 wątków jednocześnie.

Jeśli obiekt jest zapisywana przez jeden wątek, następnie wszystkich operacji odczytu i zapisu do tego obiektu na tym samym lub inne wątki muszą być chronione. Przykładowo podana obiektu A, jeśli wątek 1 zapisuje A, następnie wątku 2 należy uniemożliwić odczyt lub zapis do serwera A.

Jest to bezpieczne odczytu i zapisu w jedno wystąpienie typu, nawet jeśli inny wątek jest odczytu lub zapisu do innego wystąpienia tego samego typu. Przykładowo podana obiektów, A i B tego samego typu, jest bezpieczne podczas zapisywania w wątku 1 A i B odczytu w wątku 2.

## <a name="sharedptr"></a>shared_ptr

Wiele wątków można jednocześnie odczytu i zapisu różnych [shared_ptr](../standard-library/shared-ptr-class.md) obiektów, nawet wtedy, gdy obiekty są kopie, które mają prawo własności.

## <a name="iostream"></a>iostream

Obiekty standardowe iostream `cin`, `cout`, `cerr`, `clog`, `wcin`, `wcout`, `wcerr`, i `wclog` są zgodne z regułami innych klas, z tym wyjątkiem: bezpiecznie zapis do obiektu z wielu wątków. Na przykład może zapisać wątku 1 [cout](../standard-library/iostream.md#cout) w tym samym czasie jako wątku 2. Jednak może to spowodować dane wyjściowe z dwoma wątkami na się zmieszać.

> [!NOTE]
> Odczytywanie z buforu strumienia nie jest uważany za operacji odczytu. Zamiast tego jest on uznawany za można operacji zapisu, ponieważ stan klasy zostanie zmieniona.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
