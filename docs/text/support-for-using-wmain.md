---
title: Obsługa używania funkcji wmain | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- wWinMain
dev_langs:
- C++
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 390f2a11b98a851b5f33b4e0a941a515421d5836
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011620"
---
# <a name="support-for-using-wmain"></a>Obsługa używania funkcji wmain
Visual C++ obsługuje definiowanie **wmain** funkcji i przekazanie argumentów do znaków dwubajtowych do aplikacji Unicode. Możesz deklarować Parametry formalne dla **wmain**, za pomocą format podobny do `main`. Możesz następnie przekazać argumenty znaków dwubajtowych i, opcjonalnie, wskaźnik znaku dwubajtowego środowiska do programu. `argv` i `envp` parametry **wmain** typu `wchar_t*`. Na przykład:  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
> [!NOTE]
>  Użyj aplikacji nieobsługujących kodu Unicode w MFC `wWinMain` jako punkt wejścia. W tym przypadku `CWinApp::m_lpCmdLine` jest ciąg Unicode. Pamiętaj ustawić `wWinMainCRTStartup` z [/Entry](../build/reference/entry-entry-point-symbol.md) — opcja konsolidatora.  
  
 Jeśli program używa `main` funkcji środowiska znak wielobajtowy jest tworzony przez biblioteki wykonawczej w momencie uruchamiania programu. Tworzona jest kopia znaków dwubajtowych, środowiska, tylko wtedy, gdy jest to wymagane (na przykład przez wywołanie `_wgetenv` lub `_wputenv` funkcji). W pierwszym wywołaniu `_wputenv`, lub na pierwszym wywołaniu `_wgetenv` Jeśli środowisko MBCS już istnieje, zostanie utworzony odpowiedniego środowiska ciąg znaków dwubajtowych. Środowisko jest następnie wskazywany przez `_wenviron` zmienna globalna, która jest wersją znaków dwubajtowych z `_environ` zmiennej globalnej. W tym momencie dwie kopie środowiska (MBCS i Unicode) mogły współistnieć i są obsługiwane przez system środowiska wykonawczego w całym cyklu życia programu.  
  
 Podobnie jeśli program używa **wmain** funkcji, jest tworzony w momencie uruchamiania programu środowiska szerokich znaków i jest wskazywany przez `_wenviron` zmiennej globalnej. Środowisko MBCS (ASCII) jest tworzona przy pierwszym wywołaniu do `_putenv` lub `getenv` i jest wskazywany przez `_environ` zmiennej globalnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa formatu Unicode](../text/support-for-unicode.md)   
 [Podsumowanie programowania Unicode](../text/unicode-programming-summary.md)   
 [Funkcja WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559)