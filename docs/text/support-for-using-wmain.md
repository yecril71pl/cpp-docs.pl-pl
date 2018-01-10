---
title: "Obsługa używania funkcji wmain | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: wWinMain
dev_langs: C++
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 721915ca5ebbc75b17771dae0804e94aa360177c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="support-for-using-wmain"></a>Obsługa używania funkcji wmain
Visual C++ obsługuje definiowanie **wmain** funkcji i przekazywanie argumentów znaków dwubajtowych w aplikacji Unicode. Deklarowanie parametrów formalnych do **wmain**, używając formatu podobnego do **głównego**. Następnie można przekazać argumenty znaków dwubajtowych i, opcjonalnie, wskaźnik znaków dwubajtowych środowiska do programu. `argv` i `envp` parametry **wmain** typu `wchar_t*`. Na przykład:  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
> [!NOTE]
>  Aplikacje MFC Unicode używać **wWinMain** jako punkt wejścia. W takim przypadku `CWinApp::m_lpCmdLine` jest ciągiem Unicode. Należy ustawić **wWinMainCRTStartup** z [/Entry](../build/reference/entry-entry-point-symbol.md) — opcja konsolidatora.  
  
 Jeśli używany przez program **głównego** funkcji środowiska znaków wielobajtowych jest tworzony przez biblioteki wykonawczej w momencie uruchamiania programu. Zostanie utworzona kopia znaków dwubajtowych środowiska, tylko w razie potrzeby (na przykład przez wywołanie do `_wgetenv` lub `_wputenv` funkcji). W pierwszym wywołaniu `_wputenv`, lub w pierwszym wywołaniu `_wgetenv` Jeśli środowisko MBCS już istnieje, zostanie utworzony odpowiednie środowisko ciąg znaków dwubajtowych. Środowisko jest następnie wskazywana przez `_wenviron` zmiennej globalnej, który jest wersją znaków dwubajtowych z `_environ` zmiennej globalnej. W tym momencie dwie kopie środowiska (MBCS i Unicode) istnieje jednocześnie i mają być przechowywane przez cały czas życia program system czasu wykonywania.  
  
 Podobnie jeśli jest używany przez program **wmain** funkcji, jest tworzony w momencie uruchamiania programu środowiska znaków dwubajtowych i jest wskazywana przez `_wenviron` zmiennej globalnej. Środowisko MBCS (ASCII) jest tworzony w pierwszym wywołaniu `_putenv` lub `getenv` i jest wskazywana przez `_environ` zmiennej globalnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa formatu Unicode](../text/support-for-unicode.md)   
 [Podsumowanie programowania Unicode](../text/unicode-programming-summary.md)   
 [WinMain — funkcja](http://msdn.microsoft.com/library/windows/desktop/ms633559)