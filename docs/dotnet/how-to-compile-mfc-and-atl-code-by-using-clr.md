---
title: "Porady: kompilacja MFC i ATL kodu za pomocą - clr | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], interoperability
- ATL [C++], interoperability
- mixed assemblies [C++], MFC code
- mixed assemblies [C++], ATL code
- /clr compiler option [C++], compiling ATL and MFC code
- interoperability [C++], /clr compiler option
- regular MFC DLLs [C++], /clr compiler option
- interop [C++], /clr compiler option
- extension DLLs [C++], /clr compiler option
ms.assetid: 12464bec-33a4-482c-880a-c078de7f6ea5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f03e324cf4f88d47232cba5e15ec65181af91feb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>Porady: kompilowanie kodu MFC i ATL za pomocą opcji /clr
W tym temacie omówiono sposób kompilowania istniejących programów MFC i ATL pod kątem środowisko uruchomieniowe języka wspólnego.  
  
### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>Aby skompilować MFC pliku wykonywalnego lub regularnych bibliotek DLL MFC za pomocą/CLR  
  
1.  Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** , a następnie kliknij przycisk **właściwości**.  
  
2.  W **właściwości projektu** okna dialogowego rozwiń węzeł obok **właściwości konfiguracji** i wybierz **ogólne**. W prawym okienku w obszarze **domyślne projektu**, ustaw **Obsługa środowisko uruchomieniowe języka wspólnego** do **obsługuje wspólnego języka środowiska uruchomieniowego (/ clr)**.  
  
     Upewnij się, że w tym samym okienku **Użyj MFC** ustawiono **Użyj MFC w bibliotece DLL udostępnionych**.  
  
3.  W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. Upewnij się, że **Format informacji debugowania** ustawiono **/zi bazy danych programu** (nie **/zi**).  
  
4.  Wybierz **generowania kodu** węzła. Ustaw **włączyć minimalna ponowna kompilacja** do **nr (/ Gm-)**. Również ustawić **podstawowe Sprawdzanie czasu wykonania** do **domyślne**.  
  
5.  W obszarze **właściwości konfiguracji**, wybierz pozycję **C/C++** , a następnie **generowania kodu**. Upewnij się, że **biblioteki wykonawczej** jest ustawiona jako **Multi-threaded DLL debugowania (/ MDd)** lub **Multi-threaded DLL (/ MD)**.  
  
6.  W pliku Stdafx.h Dodaj następujący wiersz.  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>Aby skompilować rozszerzenia MFC DLL za pomocą/CLR  
  
1.  Postępuj zgodnie z instrukcjami "Aby skompilować MFC pliku wykonywalnego lub regularnych bibliotek DLL MFC za pomocą/CLR".  
  
2.  W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **prekompilowanych nagłówków**. Ustaw **Utwórz/Użyj Prekompilowanego nagłówka** do **nie używa prekompilowanych nagłówków**.  
  
     Alternatywnie w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy Stdafx.cpp, a następnie kliknij przycisk **właściwości**. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. Ustaw **Kompiluj ze wsparciem środowiska CLR** do **wsparciem środowiska CLR nie**.  
  
3.  Dla pliku, który zawiera funkcji DllMain i wykonywanych wywołuje, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik, a następnie kliknij przycisk **właściwości**. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. W prawym okienku w obszarze **domyślne projektu**ustaw **Kompiluj ze wsparciem środowiska CLR** do **wsparciem środowiska CLR nie**.  
  
### <a name="to-compile-an-atl-executable-by-using-clr"></a>Aby skompilować pliku wykonywalnego ATL za pomocą/CLR  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**.  
  
2.  W **właściwości projektu** okna dialogowego rozwiń węzeł obok **właściwości konfiguracji** i wybierz **ogólne**. W prawym okienku w obszarze **domyślne projektu**, ustaw **Obsługa środowisko uruchomieniowe języka wspólnego** do **obsługuje wspólnego języka środowiska uruchomieniowego (/ clr)**.  
  
3.  W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. Upewnij się, że **Format informacji debugowania** ustawiono **/zi bazy danych programu** (nie **/zi**).  
  
4.  Wybierz **generowania kodu** węzła. Ustaw **włączyć minimalna ponowna kompilacja** do **nr (/ Gm-)**. Również ustawić **podstawowe Sprawdzanie czasu wykonania** do **domyślne**.  
  
5.  W obszarze **właściwości konfiguracji**, wybierz pozycję **C/C++** , a następnie **generowania kodu**. Upewnij się, że **biblioteki wykonawczej** jest ustawiona jako **Multi-threaded DLL debugowania (/ MDd)** lub **Multi-threaded DLL (/ MD)**.  
  
6.  Dla każdego pliku generowanych przez MIDL (pliki C), kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań** , a następnie kliknij przycisk **właściwości**. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. Ustaw **Kompiluj ze wsparciem środowiska CLR** do **wsparciem środowiska CLR nie**.  
  
### <a name="to-compile-an-atl-dll-by-using-clr"></a>Aby skompilować ATL DLL za pomocą/CLR  
  
1.  Wykonaj kroki opisane w sekcji "Aby skompilować pliku wykonywalnego ATL za pomocą/CLR".  
  
2.  W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **prekompilowanych nagłówków**. Ustaw **Utwórz/Użyj Prekompilowanego nagłówka** do **nie używa prekompilowanych nagłówków**.  
  
     Alternatywnie w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy Stdafx.cpp, a następnie kliknij przycisk **właściwości**. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. Ustaw **Kompiluj ze wsparciem środowiska CLR** do **wsparciem środowiska CLR nie**.  
  
3.  Dla pliku, który zawiera funkcji DllMain i wykonywanych wywołuje, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik, a następnie kliknij przycisk **właściwości**. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. W prawym okienku w obszarze **domyślne projektu**ustaw **Kompiluj ze wsparciem środowiska CLR** do **wsparciem środowiska CLR nie**.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)