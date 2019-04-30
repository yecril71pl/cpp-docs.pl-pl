---
title: Dodatkowe zagadnienia dotyczące uruchamiania
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
ms.openlocfilehash: 16e48f2e4f7544d28a1bea00e1fdf2d1cff397b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385079"
---
# <a name="additional-startup-considerations"></a>Dodatkowe zagadnienia dotyczące uruchamiania

W języku C++ obiekt konstrukcje i zniszczenie ruchu może obejmować wykonywanie kodu użytkownika. Dlatego jest ważne, aby zrozumieć, które inicjalizacje się odbyć przed wpis, aby `main` i które destruktory są wywoływane po wyjściu z `main`. (Aby uzyskać szczegółowe informacje dotyczące budowa i niszczenie obiektów, zobacz [konstruktory](../cpp/constructors-cpp.md) i [destruktory](../cpp/destructors-cpp.md).)

Następujące inicjowanie odbywać się przed wejściem do `main`:

- Domyślna inicjalizacja danych statycznych do zera. Wszystkie dane statyczne, bez jawnego inicjatory są ustawiane na zero, przed wykonaniem wszelkich innych kodu, w tym inicjowania środowiska wykonawczego. Statyczne elementy członkowskie danych nadal muszą być jawnie zdefiniowane.

- Inicjowanie statycznych obiektów globalnych w jednostce translacji. Taka sytuacja może wystąpić przed wpis `main` lub przed pierwszym użyciem dowolnej funkcji lub obiektu w jednostce translacji obiektu.

**Microsoft Specific**

W Microsoft C++, obiekty globalne statyczne są inicjowane przed wejściem do `main`.

**END specyficzny dla Microsoft**

Statycznych obiektów globalnych, które są wzajemnie się wzajemnie, ale w jednostki translacji różnych mogą spowodować niepoprawne zachowanie.

## <a name="see-also"></a>Zobacz także

[Uruchomienie i zakończenie](../cpp/startup-and-termination-cpp.md)