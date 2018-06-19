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
ms.openlocfilehash: ece834bd6bf85daacbbaf50110e6e278da1ae099
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686935"
---
# <a name="multithread-programs"></a>Programy wielowątkowe
Wątek jest zasadniczo ścieżka wykonywania za pośrednictwem programu. Istnieje również najmniejsza wykonanie, które planuje Win32. Wątek składa się z stosu, stan rejestrów Procesora i wpis na liście wykonywania Harmonogram systemu. Każdy wątek udostępnia zasoby wszystkich procesów.  
  
 Proces składa się z co najmniej jeden wątek i kod, danych i innych zasobów programu w pamięci. Zasoby typowego programu są otwarte pliki, semaforów i dynamicznej alokacji pamięci. Program wykonuje się, gdy Harmonogram systemu zapewnia jeden z wątków wykonywania. Harmonogram Określa wątków, które powinno być ono uruchomione i kiedy powinno być ono uruchomione. Wątki niższego priorytetu może być konieczne Zaczekaj, aż wyższy priorytet wątków wykonywania swoich zadań. Na komputerach wieloprocesorowych harmonogram można przenieść poszczególne wątki różnych procesorów, aby równoważyć obciążenie procesora CPU.  
  
 Każdy wątek w procesie działa niezależnie. Jeśli nie możesz wyświetlić je ze sobą, wątki wykonaj indywidualnie i znają innych wątków w procesie. Udostępnianie wspólnych zasobów wątków jednak musi koordynować pracę przy użyciu semaforów lub innej metody komunikacji międzyprocesowej. Aby uzyskać więcej informacji na temat synchronizacja wątków, zobacz [zapisywania wielowątkowe programu systemu Win32](../parallel/writing-a-multithreaded-win32-program.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)