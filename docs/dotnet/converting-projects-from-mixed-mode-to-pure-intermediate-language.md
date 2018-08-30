---
title: Konwertowanie projektów z mieszany tryb na czysty język bezpośredni | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 263a90710d2103c4ea97e6c56da67d676ba7366b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222083"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Konwertowanie projektów z trybu mieszanego na czysty język bezpośredni

Wszystkie projekty Visual C++ CLR łącze do biblioteki wykonawczej C domyślnie. W związku z tym te projekty są klasyfikowane jako aplikacji w trybie mieszanym, ponieważ łączą w sobie kod natywny kod, który jest przeznaczony dla środowiska uruchomieniowego języka wspólnego (kod zarządzany). Gdy są one kompilowane, są one kompilowane do języka pośredniego (IL), znany także jako język Microsoft intermediate language (MSIL).

> [!IMPORTANT]
> Przestarzałe w programie Visual Studio 2015 i Visual Studio 2017 już nie obsługuje tworzenia **/CLR: pure** lub **/CLR: Safe** kodu dla aplikacji do środowiska CLR. Jeśli potrzebujesz zestawy czysty lub bezpieczny, zalecamy tłumaczenie aplikacji C#.

Jeśli używasz wcześniejszej wersji zestawu narzędzi kompilatora Visual C++, która obsługuje **/CLR: pure** lub **/CLR: Safe**, można użyć tej procedury, aby przekonwertować kod czysty MSIL:

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>Aby przekonwertować aplikacji trybu mieszanego na czysty język bezpośredni

1. Usuń łącza do [biblioteki wykonawczej C](../c-runtime-library/crt-library-features.md) (CRT):

   1. Plik CPP definiujący punkt wejścia aplikacji, Zmień punkt wejścia do `Main()`. Za pomocą `Main()` wskazuje, że projekt nie zawiera linków do CRT.

   2. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz **właściwości** w menu skrótów, można otworzyć strony właściwości dla aplikacji.

   3. W **zaawansowane** strony właściwości projektu dla **konsolidatora**, wybierz opcję **punktu wejścia** , a następnie wprowadź **Main** w tym polu.

   4. Dla aplikacji konsoli w **systemu** strony właściwości projektu dla **konsolidatora**, wybierz opcję **podsystemu** pola, a następnie zmień ten element, aby **Konsola (/ Subsystem:Console)**.

      > [!NOTE]
      > Nie masz można ustawić tej właściwości dla aplikacji Windows Forms, ponieważ **podsystemu** pole jest ustawione na **Windows (/ SUBSYSTEM: WINDOWS)** domyślnie.

   5. W pliku stdafx.h komentarz wszystkich `#include` instrukcji. Na przykład w aplikacji konsoli:

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       —lub—

       Na przykład w aplikacjach Windows Forms:

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. Dla aplikacji Windows Forms w Form1.cpp, komentarz `#include` instrukcję, która odwołuje się do windows.h. Na przykład:

      ```cpp
      // #include <windows.h>
      ```

2. Dodaj następujący kod do pliku stdafx.h:

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. Usuń wszystkie typy niezarządzanwe:

   Wszędzie, gdzie jest to stosowne, Zamień typy niezarządzanwe odwołania do struktury firmy [systemu](https://msdn.microsoft.com/library/system.appdomainmanager.appdomainmanager.aspx) przestrzeni nazw. Popularne typy zarządzane są wymienione w poniższej tabeli:

   |Struktura|Opis|
   |---------------|-----------------|
   |[Boolean](https://msdn.microsoft.com/library/system.boolean\(v=vs.140\).aspx)|Reprezentuje wartość logiczną.|
   |[Byte](https://msdn.microsoft.com/library/system.byte\(v=vs.140\).aspx)|Reprezentuje 8-bitowej nieoznaczonej liczby całkowitej.|
   |[Char](https://msdn.microsoft.com/library/system.char\(v=vs.140\).aspx)|Reprezentuje znak Unicode.|
   |[DateTime](https://msdn.microsoft.com/library/system.datetime.datetime.aspx)|Reprezentuje moment w czasie, zwykle wyrażona jako datę i godzinę.|
   |[Decimal](https://msdn.microsoft.com/library/system.decimal\(v=vs.140\).aspx)|Reprezentuje liczbę dziesiętną.|
   |[Double](https://msdn.microsoft.com/library/system.double\(v=vs.140\).aspx)|Reprezentuje liczbę zmiennoprzecinkową podwójnej precyzji.|
   |[Identyfikator GUID](https://msdn.microsoft.com/library/system.guid\(v=vs.140\).aspx)|Reprezentuje unikatowy identyfikator globalny (GUID).|
   |[Int16](https://msdn.microsoft.com/library/system.int16\(v=vs.140\).aspx)|Reprezentuje całkowita 16-bitowych.|
   |[Int32](https://msdn.microsoft.com/library/system.int32\(v=vs.140\).aspx)|Reprezentuje całkowita 32-bitowych.|
   |[Int64](https://msdn.microsoft.com/library/system.int64\(v=vs.140\).aspx)|Reprezentuje całkowita 64-bitowych.|
   |[Pola IntPtr](https://msdn.microsoft.com/library/system.intptr\(v=vs.140\).aspx)|Typ specyficzny dla platformy, który jest używany do reprezentowania wskaźnika lub uchwytu.|
   |[SByte](https://msdn.microsoft.com/library/system.byte.aspx)|Reprezentuje całkowita 8-bitowych.|
   |[Single](https://msdn.microsoft.com/library/system.single.aspx)|Reprezentuje liczbę zmiennoprzecinkową pojedynczej precyzji.|
   |[TimeSpan](https://msdn.microsoft.com/library/system.timespan\(v=vs.140\).aspx)|Reprezentuje przedział czasu.|
   |[UInt16](https://msdn.microsoft.com/library/system.uint16\(v=vs.140\).aspx)|Reprezentuje 16-bitowa liczba całkowita bez znaku.|
   |[UInt32](https://msdn.microsoft.com/library/system.uint32\(v=vs.140\).aspx)|Reprezentuje 32-bitowa liczba całkowita bez znaku.|
   |[UInt64 —](https://msdn.microsoft.com/library/system.uint64\(v=vs.140\).aspx)|Reprezentuje 64-bitowej nieoznaczonej liczby całkowitej.|
   |[UIntPtr](https://msdn.microsoft.com/library/system.uintptr\(v=vs.140\).aspx)|Typ specyficzny dla platformy, który jest używany do reprezentowania wskaźnika lub uchwytu.|
   |[Void](https://msdn.microsoft.com/library/system.void\(v=vs.140\).aspx)|Wskazuje metodę, która nie zwraca wartości; oznacza to, że metoda ma zwracać typ void.|