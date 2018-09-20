---
title: Programy wielowątkowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88c39590f27597d29a27ab60bbc95c3c46dc862c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416867"
---
# <a name="multithread-programs"></a>Programy wielowątkowe

Wątek jest zasadniczo ścieżką wykonywania programu. Jest również najmniejsza jednostka wykonania, która planuje Win32. Wątek składa się ze stosu, stan rejestry procesora CPU i wpis na liście wykonywania harmonogramu systemu. Każdy wątek współdzielą zasoby wszystkich procesów.

Proces składa się z jednego lub więcej wątków i kod, danych i inne zasoby programu w pamięci. Zasoby programu typowe są otwarte pliki, semaforów i pamięć przydzielana dynamicznie. Program wykonuje, gdy Harmonogram systemu zawiera jeden z wątków Kontrola wykonywania. Harmonogram Określa, które wątki powinno być ono uruchomione i kiedy powinno być ono uruchomione. Wątki niższego priorytetu może być konieczne Zaczekaj, aż wyższy priorytet wątków wykonania swoich zadań. Na komputerach wieloprocesorowych harmonogram można przenieść określonych wątków do różnych procesorów, aby równoważyć obciążenie procesora CPU.

Każdy wątek w procesie działa niezależnie od siebie. Jeśli nie możesz je uwidocznić ze sobą, wątki wykonaj indywidualnie i znają inne wątki w procesie. Wątki Udostępnianie wspólnych zasobów, jednak należy koordynować wzajemnie swoją pracę za pomocą semaforów lub innej metody komunikacji międzyprocesowej. Aby uzyskać więcej informacji na temat synchronizowania wątków, zobacz [pisanie wielowątkowego programu Win32](writing-a-multithreaded-win32-program.md).

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)