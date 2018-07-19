---
title: Łączenie z CRT w projekcie ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- DllMainCRTStartup
- wWinMainCRTStartup
- WinMainCRTStartup
dev_langs:
- C++
helpviewer_keywords:
- CRT, linking with ATL
- WinMainCRTStartup method
- DllMainCRTStartup method
- wWinMainCRTStartup method
- ATL, C Run-Time library (CRT)
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad8209c680a782bd9800215e1e0affc7e2a98c8
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852500"
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>Łączenie z CRT w projekcie ATL
[C Run-Time Libraries](../c-runtime-library/crt-library-features.md) (CRT) zapewniają wiele przydatnych funkcji, które mogą ułatwić programowania znacznie łatwiejsze, podczas tworzenia biblioteki ATL. Wszystkie projekty ATL łącze do biblioteki CRT. Widać, zalety i wady łączenie method in Class metoda [zalety i wady metody używane do tworzenia linków do CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md).  
  
## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>Skutki łączenia z CRT na obrazie programu  
 Jeśli połączysz się statycznie CRT, kodu z CRT znajduje się w pliku wykonywalnego obrazu i nie musisz mieć DLL CRT obecne w systemie do uruchomienia obrazu. Jeśli dynamicznie połączysz do CRT, odwołania do kodu w bibliotece DLL CRT, są umieszczane w obrazie, ale nie sam kod. Aby obraz do uruchamiania w danym systemie biblioteki DLL CRT musi występować w tym systemie. Nawet jeśli dynamicznie połączysz CRT, może się okazać, że kodu mogą być połączone statycznie (na przykład `DllMainCRTStartup`).  
  
 Gdy łączysz obraz, należy jawnie lub niejawnie określić punkt wejścia, który system operacyjny będzie wywoływać po załadowaniu obrazu. Jest domyślny punkt wejścia biblioteki DLL, `DllMainCRTStartup`. W przypadku pliku EXE, jest `WinMainCRTStartup`. Można zastąpić domyślną przy użyciu opcji konsolidatora/Entry. CRT udostępnia implementację na potrzeby `DllMainCRTStartup`, `WinMainCRTStartup`, i `wWinMainCRTStartup` (Unicode punkt wejścia dla pliku EXE). Te punkty wejścia podana do CRT wywoływać konstruktorów do obiektów globalnych i zainicjuj innych struktur danych, które są używane przez niektóre funkcje CRT. Ten kod startowy dodaje około 25 tys. do obrazu, jeśli jest połączona statycznie. Jeśli jest połączona dynamicznie, większość kodu jest w tej bibliotece DLL, więc rozmiaru obrazu pozostaje małe.  
  
 Aby uzyskać więcej informacji, zobacz temat konsolidatora [/Entry (Symbol punktu wejścia)](../build/reference/entry-entry-point-symbol.md).  
  
## <a name="optimization-options"></a>Opcje optymalizacji  
 Przy użyciu opcji konsolidatora nowin98 może dodatkowo ograniczyć domyślny formant ATL o 10 K na expense z zwiększyć czas w systemach Windows 98 ładowania. Aby uzyskać więcej informacji na temat łączenia opcji, zobacz [od (optymalizacje)](../build/reference/opt-optimizations.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą kodu ATL i C Run-Time](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Zachowanie biblioteki wykonawczej DLL i Visual C++](../build/run-time-library-behavior.md)

