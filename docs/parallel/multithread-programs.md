---
title: "Programy wielowątkowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: effbb235ef678253f5258d3eb01a3a82292385cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="multithread-programs"></a>Programy wielowątkowe
Wątek jest zasadniczo ścieżka wykonywania za pośrednictwem programu. Istnieje również najmniejsza wykonanie, które planuje Win32. Wątek składa się z stosu, stan rejestrów Procesora i wpis na liście wykonywania Harmonogram systemu. Każdy wątek udostępnia zasoby wszystkich procesów.  
  
 Proces składa się z co najmniej jeden wątek i kod, danych i innych zasobów programu w pamięci. Zasoby typowego programu są otwarte pliki, semaforów i dynamicznej alokacji pamięci. Program wykonuje się, gdy Harmonogram systemu zapewnia jeden z wątków wykonywania. Harmonogram Określa wątków, które powinno być ono uruchomione i kiedy powinno być ono uruchomione. Wątki niższego priorytetu może być konieczne Zaczekaj, aż wyższy priorytet wątków wykonywania swoich zadań. Na komputerach wieloprocesorowych harmonogram można przenieść poszczególne wątki różnych procesorów, aby równoważyć obciążenie procesora CPU.  
  
 Każdy wątek w procesie działa niezależnie. Jeśli nie możesz wyświetlić je ze sobą, wątki wykonaj indywidualnie i znają innych wątków w procesie. Udostępnianie wspólnych zasobów wątków jednak musi koordynować pracę przy użyciu semaforów lub innej metody komunikacji międzyprocesowej. Aby uzyskać więcej informacji na temat synchronizacja wątków, zobacz [zapisywania wielowątkowe programu systemu Win32](../parallel/writing-a-multithreaded-win32-program.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z C i Win32](../parallel/multithreading-with-c-and-win32.md)