---
title: 'Instrukcje: Kompilowanie kodu MFC i ATL za pomocą opcji / clr'
ms.custom: get-started-article
ms.date: 11/04/2016
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
ms.openlocfilehash: 9a24e82787eb0fce8ff668843e73de9f2d05e1ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379053"
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>Instrukcje: Skompilować MFC i ATL kodu za pomocą/CLR

W tym temacie omówiono sposób kompilowania istniejących programów MFC i ATL do docelowe środowisko uruchomieniowe języka wspólnego.

### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>Aby skompilować MFC pliku wykonywalnego lub regularnych biblioteki MFC DLL za pomocą/CLR

1. Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** a następnie kliknij przycisk **właściwości**.

1. W **właściwości projektu** okna dialogowego, rozwiń węzeł obok **właściwości konfiguracji** i wybierz **ogólne**. W okienku po prawej stronie w obszarze **domyślne wartości projektu**ustaw **Obsługa środowiska uruchomieniowego języka wspólnego** do **wsparcie (/ clr)**.

   Upewnij się, że w tym samym okienku **użycie MFC** ustawiono **Użyj MFC w współdzielonej bibliotece DLL**.

1. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. Upewnij się, że **formatu informacji debugowania** ustawiono **/zi bazy danych programu** (nie **/zi**).

1. Wybierz **generowania kodu** węzła. Ustaw **Włącz minimalną ponowną kompilację** do **nr (/ Gm-)**. Również ustawić **podstawowe sprawdzenia środowiska uruchomieniowego** do **domyślne**.

1. W obszarze **właściwości konfiguracji**, wybierz opcję **C/C++** i następnie **generowania kodu**. Upewnij się, że **biblioteki środowiska uruchomieniowego** jest ustawiona jako **Multi-threaded DLL debugowania (/ MDd)** lub **Multi-threaded biblioteki DLL (/ MD)**.

1. W pliku Stdafx.h należy dodać następujący wiersz.

    ```
    #using <System.Windows.Forms.dll>
    ```

### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>Aby skompilować rozszerzenia MFC biblioteki DLL za pomocą/CLR

1. Wykonaj kroki opisane w "Aby skompilować MFC pliku wykonywalnego lub regularnych biblioteki MFC DLL za pomocą/CLR".

1. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **prekompilowanych nagłówków**. Ustaw **Utwórz/użycie Prekompilowanego nagłówka** do **nie używa prekompilowanych nagłówków**.

   Jako alternatywę w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy Stdafx.cpp, a następnie kliknij przycisk **właściwości**. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. Ustaw **skompilować z obsługą środowiska uruchomieniowego języka wspólnego** do **Obsługa środowiska uruchomieniowego języka wspólnego nie**.

1. Dla pliku, który zawiera funkcji DllMain i nic wywoływanych przez nią, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik, a następnie kliknij przycisk **właściwości**. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. W okienku po prawej stronie w obszarze **domyślne wartości projektu**ustaw **skompilować z obsługą środowiska uruchomieniowego języka wspólnego** do **Obsługa środowiska uruchomieniowego języka wspólnego nie**.

### <a name="to-compile-an-atl-executable-by-using-clr"></a>Aby skompilować plik wykonywalny ATL za pomocą/CLR

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**.

1. W **właściwości projektu** okna dialogowego, rozwiń węzeł obok **właściwości konfiguracji** i wybierz **ogólne**. W okienku po prawej stronie w obszarze **domyślne wartości projektu**ustaw **Obsługa środowiska uruchomieniowego języka wspólnego** do **wsparcie (/ clr)**.

1. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. Upewnij się, że **formatu informacji debugowania** ustawiono **/zi bazy danych programu** (nie **/zi**).

1. Wybierz **generowania kodu** węzła. Ustaw **Włącz minimalną ponowną kompilację** do **nr (/ Gm-)**. Również ustawić **podstawowe sprawdzenia środowiska uruchomieniowego** do **domyślne**.

1. W obszarze **właściwości konfiguracji**, wybierz opcję **C/C++** i następnie **generowania kodu**. Upewnij się, że **biblioteki środowiska uruchomieniowego** jest ustawiona jako **Multi-threaded DLL debugowania (/ MDd)** lub **Multi-threaded biblioteki DLL (/ MD)**.

1. Dla każdego pliku MIDL generowane (pliki C), kliknij prawym przyciskiem myszy plik w **Eksploratora rozwiązań** a następnie kliknij przycisk **właściwości**. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. Ustaw **skompilować z obsługą środowiska uruchomieniowego języka wspólnego** do **Obsługa środowiska uruchomieniowego języka wspólnego nie**.

### <a name="to-compile-an-atl-dll-by-using-clr"></a>Aby skompilować ATL DLL za pomocą/CLR

1. Wykonaj kroki opisane w sekcji "Aby skompilować pliku wykonywalnego ATL za pomocą/CLR".

1. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **prekompilowanych nagłówków**. Ustaw **Utwórz/użycie Prekompilowanego nagłówka** do **nie używa prekompilowanych nagłówków**.

   Jako alternatywę w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy Stdafx.cpp, a następnie kliknij przycisk **właściwości**. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. Ustaw **skompilować z obsługą środowiska uruchomieniowego języka wspólnego** do **Obsługa środowiska uruchomieniowego języka wspólnego nie**.

1. Dla pliku, który zawiera funkcji DllMain i nic wywoływanych przez nią, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik, a następnie kliknij przycisk **właściwości**. W obszarze **właściwości konfiguracji**, rozwiń węzeł obok **C/C++** i wybierz **ogólne**. W okienku po prawej stronie w obszarze **domyślne wartości projektu**ustaw **skompilować z obsługą środowiska uruchomieniowego języka wspólnego** do **Obsługa środowiska uruchomieniowego języka wspólnego nie**.

## <a name="see-also"></a>Zobacz także

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
