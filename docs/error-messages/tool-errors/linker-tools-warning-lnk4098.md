---
title: "Ostrzeżenie LNK4098 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4098
dev_langs:
- C++
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b199c19417d7d3be866109fff7361fb4ead959d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4098"></a>Ostrzeżenie LNK4098 narzędzi konsolidatora
Użyj "library" defaultlib w konflikcie z innymi bibliotekami; Użyj /NODEFAULTLIB:library  
  
 Próbujesz się połączyć z bibliotekami niezgodne.  
  
> [!NOTE]
>  Biblioteki wykonawcze zawierają teraz dyrektywy, aby zapobiec mieszaniu różnych typów. W ten sam program otrzymasz to ostrzeżenie, Jeśli spróbujesz użyć różnych typów lub debugowania i bez debugowania wersji biblioteki czasu wykonywania. Na przykład jeśli skompilowany jeden plik do korzystania z jednego rodzaju biblioteki wykonawczej języka innego pliku używać innego typu (na przykład jednowątkowe i wielowątkowe) i próbował łączyć je, otrzymasz to ostrzeżenie. Należy skompilować wszystkie pliki źródłowe do korzystania z tej samej biblioteki czasu wykonywania. Zobacz [biblioteki wykonawczej użyj](../../build/reference/md-mt-ld-use-run-time-library.md) (**/ / MD**, **/MT**, **/LD**) opcje kompilatora, aby uzyskać więcej informacji.  
  
 Można użyć konsolidatora [: lib](../../build/reference/verbose-print-progress-messages.md) przełącznik, aby określić, które wyszukuje konsolidator biblioteki. Jeśli zostanie wyświetlony LNK4098, aby utworzyć plik wykonywalny, który używa, na przykład jednowątkowe, bez debugowania biblioteki czasu wykonywania, użyj **: lib** opcję, aby dowiedzieć się, które wyszukuje konsolidator biblioteki. Konsolidator wydrukować LIBC.lib i nie LIBCMT.lib MSVCRT.lib, LIBCD.lib, LIBCMTD.lib albo MSVCRTD.lib jako przeszukiwane biblioteki. Można ustalić konsolidator, aby zignorować niepoprawne biblioteki czasu wykonywania przy użyciu [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) dla każdej biblioteki, aby zignorować.  
  
 W poniższej tabeli przedstawiono, które biblioteki należy ją ignorować w zależności od biblioteki wykonawczej, którego chcesz użyć.  
  
|Aby użyć tej biblioteki wykonawczej|Ignoruj biblioteki|  
|-----------------------------------|----------------------------|  
|Jednowątkowe (libc.lib)|libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|Wielowątkowe (libcmt.lib)|libc.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|Wielowątkowe, za pomocą biblioteki DLL (msvcrt.lib)|libc.lib, libcmt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|  
|Jednowątkowe debugowania (libcd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcmtd.lib, msvcrtd.lib|  
|Debugowanie wielowątkowe (libcmtd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, msvcrtd.lib|  
|Debugowanie Multithreaded za pomocą biblioteki DLL (msvcrtd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib|  
  
 Na przykład jeśli chcesz utworzyć plik wykonywalny, który jest używana bez debugowania, jednowątkowych wersja biblioteki wykonawczej Odebrano to ostrzeżenie, można użyć następujących opcji z konsolidator:  
  
```  
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib  
```