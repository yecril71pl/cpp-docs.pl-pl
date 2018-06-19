---
title: Łączenie z CRT w ATL projektu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ec0d93f8770ebbd893491c0e8b8eed239396e00a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356386"
---
# <a name="linking-to-the-crt-in-your-atl-project"></a>Łączenie z CRT w ATL projektu
[Biblioteki wykonawcze języka C](../c-runtime-library/crt-library-features.md) (CRT) zapewniają wiele przydatne funkcje, które mogą ułatwić programowania w języku znacznie podczas tworzenia biblioteki ATL. Wszystkie projekty ATL łącze do biblioteki CRT. Widać zalety i wady łączenie metody w [zalety i wady i zalety używania metody do łącza do CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md).  
  
## <a name="effects-of-linking-to-the-crt-on-your-program-image"></a>Efekty łączenia CRT w obrazie programu  
 Jeśli statycznie łączyć się CRT, kod z CRT znajduje się w pliku wykonywalnego obrazu i nie trzeba mieć DLL CRT obecne w systemie do uruchomienia obrazu. Jeśli dynamicznie połączyć CRT odwołania do kodu w bibliotece DLL CRT są umieszczane w obrazu, ale nie kod. Aby obrazu do uruchamiania w danym systemie biblioteki DLL CRT musi występować w tym systemie. Nawet jeśli zostanie dynamicznie połączony CRT, może się okazać, że niektóre kodu mogą być połączone statycznie (na przykład **DllMainCRTStartup**).  
  
 Po połączeniu obrazu jawnie lub niejawnie określisz punkt wejścia, który system operacyjny zostanie wywołany po załadowaniu obrazu. Jest domyślny punkt wejścia biblioteki DLL, **DllMainCRTStartup**. W przypadku pliku EXE, jest **WinMainCRTStartup**. Można zastąpić domyślną z/Entry — opcja konsolidatora. CRT udostępnia implementację dla **DllMainCRTStartup**, **WinMainCRTStartup**, i **wWinMainCRTStartup** (Unicode punkt wejścia dla pliku EXE). Te punkty wejścia dostarczane CRT wywoływać konstruktorów obiektów globalnych i zainicjuj inne struktury danych, które są używane przez niektóre funkcje CRT. Ten kod uruchomienia dodaje około 25K do obrazu, jeśli jest ono statycznie połączone. Jeśli jest połączona dynamicznie, większość kodu jest w bibliotece DLL, więc pozostaje mały rozmiar obrazu.  
  
 Aby uzyskać więcej informacji, zobacz temat konsolidatora [/Entry (Symbol punktu wejścia)](../build/reference/entry-entry-point-symbol.md).  
  
## <a name="optimization-options"></a>Opcje optymalizacji  
 Przy użyciu opcji konsolidatora/OPT: nowin98 można jeszcze bardziej ograniczyć formantu ATL domyślne przez 10 K, w expense z zwiększyć czas w systemach Windows 98 ładowania. Aby uzyskać więcej informacji na opcje łączenia, zobacz [od (optymalizacje)](../build/reference/opt-optimizations.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą ALT i C Run-Time kodu](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Zachowanie biblioteki wykonawczej DLL i Visual C++](../build/run-time-library-behavior.md)

