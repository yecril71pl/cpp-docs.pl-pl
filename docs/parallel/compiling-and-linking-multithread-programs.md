---
title: Kompilowanie i łączenie programów wielowątkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c77cb217fe841e15f4c7470340bd3fbb502f6a9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="compiling-and-linking-multithread-programs"></a>Kompilowanie i łączenie programów wielowątkowych
Bounce.c program została wprowadzona w systemie [przykładowy Program C wielowątkowej](../parallel/sample-multithread-c-program.md).  
  
 Programy są kompilowane wielowątkowe domyślnie.  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Aby skompilować i łączenie wielowątkowego programu Bounce.c ze środowiska programistycznego  
  
1.  Na **pliku** menu, kliknij przycisk **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W **typów projektów** okienku, kliknij przycisk **Win32**.  
  
3.  W **szablony** okienku, kliknij przycisk **aplikacji konsoli Win32**, a następnie nazwą projektu.  
  
4.  Dodaj plik zawierający kod źródłowy C do projektu.  
  
5.  Na **kompilacji** menu, skompiluj projekt, klikając **kompilacji** polecenia.  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Aby skompilować i łączenie wielowątkowego programu Bounce.c z wiersza polecenia  
  
1.  Kompilowanie i łączenie programu:  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)