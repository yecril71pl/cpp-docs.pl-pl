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
ms.openlocfilehash: 4ab667e372c8118a83b7a93444abbfbc5c19b6e0
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131521"
---
# <a name="compiling-and-linking-multithread-programs"></a>Kompilowanie i łączenie programów wielowątkowych
Bounce.c program została wprowadzona w systemie [przykładowy Program C wielowątkowości](sample-multithread-c-program.md).  
  
Programy są kompilowane wielowątkowe domyślnie.  
  
### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Aby skompilować i połącz program wielowątkowy Bounce.c w środowisku programistycznym  
  
1.  Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.  
  
2.  W **typów projektów** okienku kliknij **Win32**.  
  
3.  W **szablony** okienku kliknij **Aplikacja konsoli Win32**, a następnie nadaj projektowi nazwę.  
  
4.  Dodaj plik zawierający kod źródłowy języka C do projektu.  
  
5.  Na **kompilacji** menu, skompiluj projekt, klikając **kompilacji** polecenia.  
  
### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Aby skompilować i łączenie programów wielowątkowych Bounce.c z wiersza polecenia  
  
1.  Kompilowanie i łączenie program:  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## <a name="see-also"></a>Zobacz też

[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)