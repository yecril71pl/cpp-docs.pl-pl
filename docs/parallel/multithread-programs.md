---
title: Programy wielowątkowe
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
ms.openlocfilehash: 0b79fe84fbf7d910d53cb5bc333668b7d99ab8ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502050"
---
# <a name="multithread-programs"></a>Programy wielowątkowe

Wątek jest zasadniczo ścieżką wykonywania programu. Jest również najmniejsza jednostka wykonania, która planuje Win32. Wątek składa się ze stosu, stan rejestry procesora CPU i wpis na liście wykonywania harmonogramu systemu. Każdy wątek współdzielą zasoby wszystkich procesów.

Proces składa się z jednego lub więcej wątków i kod, danych i inne zasoby programu w pamięci. Zasoby programu typowe są otwarte pliki, semaforów i pamięć przydzielana dynamicznie. Program wykonuje, gdy Harmonogram systemu zawiera jeden z wątków Kontrola wykonywania. Harmonogram Określa, które wątki powinno być ono uruchomione i kiedy powinno być ono uruchomione. Wątki niższego priorytetu może być konieczne Zaczekaj, aż wyższy priorytet wątków wykonania swoich zadań. Na komputerach wieloprocesorowych harmonogram można przenieść określonych wątków do różnych procesorów, aby równoważyć obciążenie procesora CPU.

Każdy wątek w procesie działa niezależnie od siebie. Jeśli nie możesz je uwidocznić ze sobą, wątki wykonaj indywidualnie i znają inne wątki w procesie. Wątki Udostępnianie wspólnych zasobów, jednak należy koordynować wzajemnie swoją pracę za pomocą semaforów lub innej metody komunikacji międzyprocesowej. Aby uzyskać więcej informacji na temat synchronizowania wątków, zobacz [pisanie wielowątkowego programu Win32](writing-a-multithreaded-win32-program.md).

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)