---
title: "Konwertowanie projektów z trybu na czysty język bezpośredni mieszanego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0276d5b5420ed0294b2cf3438190f79d03585744
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Konwertowanie projektów z trybu mieszanego na czysty język bezpośredni
Wszystkie projekty Visual C++ CLR łącze do biblioteki wykonawcze języka C domyślnie. W rezultacie te projekty są sklasyfikowane jako aplikacje w trybie mieszanym, ponieważ łączą kodu natywnego z kodem, którego celem jest środowisko uruchomieniowe języka wspólnego (zarządzany kod). Gdy są one kompilowane są one kompilowane w języku pośrednim (IL), znanej także jako Microsoft język pośredni (MSIL).  
  
### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>Aby przekonwertować aplikacji trybu mieszanego na czysty język bezpośredni  
  
1.  Usuń linki do [biblioteki wykonawcze języka C](../c-runtime-library/crt-library-features.md) (CRT):  
  
    1.  W pliku .cpp Definiowanie punkt wejścia aplikacji, punkt wejścia, aby zmienić `Main()`. Przy użyciu `Main()` wskazuje, że projekt nie zawiera łączy do CRT.  
  
    2.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **właściwości** menu skrótów otwieranie stron właściwości dla aplikacji.  
  
    3.  W **zaawansowane** stronę właściwości projektu **konsolidatora**, wybierz pozycję **punktu wejścia** , a następnie wprowadź **Main** w tym polu.  
  
    4.  Dla aplikacji konsoli w **systemu** stronę właściwości projektu **konsolidatora**, wybierz pozycję **podsystemu** pola i zmień wartość na **konsoli (/ Subsystem:Console)**.  
  
        > [!NOTE]
        >  Nie masz można ustawić tej właściwości dla aplikacji formularzy systemu Windows, ponieważ **podsystemu** pole jest ustawione na **systemu Windows (/ SUBSYSTEM: WINDOWS)** domyślnie.  
  
    5.  W pliku stdafx.h, komentarz wszystkie `#include` instrukcje. Na przykład w aplikacji konsoli:  
  
        ```  
        // #include <iostream>  
        // #include <tchar.h>  
        ```  
  
         —lub—  
  
         Na przykład w aplikacji formularzy systemu Windows:  
  
        ```  
        // #include <stdlib.h>  
        // #include <malloc.h>  
        // #include <memory.h>  
        // #include <tchar.h>  
        ```  
  
    6.  Dla aplikacji Windows Forms w Form1.cpp, komentarz `#include` instrukcji, która odwołuje się do windows.h. Na przykład:  
  
        ```  
        // #include <windows.h>  
        ```  
  
2.  Dodaj następujący kod do stdafx.h:  
  
    ```  
    #ifndef __FLTUSED__  
    #define __FLTUSED__  
       extern "C" __declspec(selectany) int _fltused=1;  
    #endif  
    ```  
  
3.  Usuń wszystkie typy niezarządzanwe:  
  
    1.  W miarę potrzeb, Zamień typy niezarządzanwe odwołania do struktury z [systemu](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx) przestrzeni nazw. Popularne typy zarządzane są wymienione w poniższej tabeli:  
  
        |Struktura|Opis|  
        |---------------|-----------------|  
        |[Wartość logiczna](https://msdn.microsoft.com/en-us/library/system.boolean\(v=vs.140\).aspx)|Reprezentuje wartość logiczną.|  
        |[Bajtów](https://msdn.microsoft.com/en-us/library/system.byte\(v=vs.140\).aspx)|Reprezentuje 8-bitową nieznakowaną liczbą całkowitą.|  
        |[Char](https://msdn.microsoft.com/en-us/library/system.char\(v=vs.140\).aspx)|Reprezentuje znak Unicode.|  
        |[Data i godzina](https://msdn.microsoft.com/en-us/library/system.datetime.datetime.aspx)|Reprezentuje moment w czasie, zwykle wyrażone jako datę i godzinę.|  
        |[Decimal](https://msdn.microsoft.com/en-us/library/system.decimal\(v=vs.140\).aspx)|Reprezentuje liczbę dziesiętną.|  
        |[O podwójnej precyzji](https://msdn.microsoft.com/en-us/library/system.double\(v=vs.140\).aspx)|Reprezentuje liczbie zmiennoprzecinkowej podwójnej precyzji.|  
        |[Identyfikator GUID](https://msdn.microsoft.com/en-us/library/system.guid\(v=vs.140\).aspx)|Reprezentuje unikatowy identyfikator globalny (GUID).|  
        |[Int16](https://msdn.microsoft.com/en-us/library/system.int16\(v=vs.140\).aspx)|Reprezentuje 16-bitową liczbę całkowitą ze znakiem.|  
        |[Int32](https://msdn.microsoft.com/en-us/library/system.int32\(v=vs.140\).aspx)|Reprezentuje całkowita 32-bitowych.|  
        |[Int64](https://msdn.microsoft.com/en-us/library/system.int64\(v=vs.140\).aspx)|Reprezentuje 64-bitowej podpisanej liczby całkowitej.|  
        |[IntPtr](https://msdn.microsoft.com/en-us/library/system.intptr\(v=vs.140\).aspx)|Typ specyficzne dla platformy, który jest używany do reprezentowania wskaźnika lub dojścia.|  
        |[Sbyte —](https://msdn.microsoft.com/en-us/library/system.byte.aspx)|Reprezentuje 8-bitową liczbę całkowitą ze znakiem.|  
        |[Pojedynczy](https://msdn.microsoft.com/en-us/library/system.single.aspx)|Reprezentuje liczbie zmiennoprzecinkowej pojedynczej precyzji.|  
        |[Zakres czasu](https://msdn.microsoft.com/en-us/library/system.timespan\(v=vs.140\).aspx)|Reprezentuje przedział czasu.|  
        |[UInt16](https://msdn.microsoft.com/en-us/library/system.uint16\(v=vs.140\).aspx)|Reprezentuje 16-bitową liczbę całkowitą bez znaku.|  
        |[UInt32](https://msdn.microsoft.com/en-us/library/system.uint32\(v=vs.140\).aspx)|Reprezentuje 32-bitowej liczby całkowitej bez znaku.|  
        |[UInt64 —](https://msdn.microsoft.com/en-us/library/system.uint64\(v=vs.140\).aspx)|Reprezentuje 64-bitowej liczby całkowitej bez znaku.|  
        |[UIntPtr](https://msdn.microsoft.com/en-us/library/system.uintptr\(v=vs.140\).aspx)|Typ specyficzne dla platformy, który jest używany do reprezentowania wskaźnika lub dojścia.|  
        |[Void](https://msdn.microsoft.com/en-us/library/system.void\(v=vs.140\).aspx)|Wskazuje metodę, która nie zwraca wartości; oznacza to, że metoda ma zwrócony typ void.|