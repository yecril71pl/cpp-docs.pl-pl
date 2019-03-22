---
title: Konwertowanie projektów z trybu mieszanego na czysty język bezpośredni
ms.date: 11/04/2016
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 93eff646fb582e25ad70549afc714c5321e56079
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328587"
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

   Wszędzie, gdzie jest to stosowne, Zamień typy niezarządzanwe odwołania do struktury firmy [systemu](/dotnet/api/system) przestrzeni nazw. Popularne typy zarządzane są wymienione w poniższej tabeli:

   |Struktura|Opis|
   |---------------|-----------------|
   |[Boolean](/dotnet/api/system.boolean)|Reprezentuje wartość logiczną.|
   |[Byte](/dotnet/api/system.byte)|Reprezentuje 8-bitowej nieoznaczonej liczby całkowitej.|
   |[Char](/dotnet/api/system.char)|Reprezentuje znak Unicode.|
   |[DateTime](/dotnet/api/system.datetime)|Reprezentuje moment w czasie, zwykle wyrażona jako datę i godzinę.|
   |[Decimal](/dotnet/api/system.decimal)|Reprezentuje liczbę dziesiętną.|
   |[Double](/dotnet/api/system.double)|Reprezentuje liczbę zmiennoprzecinkową podwójnej precyzji.|
   |[Identyfikator GUID](/dotnet/api/system.guid)|Reprezentuje unikatowy identyfikator globalny (GUID).|
   |[Int16](/dotnet/api/system.int16)|Reprezentuje całkowita 16-bitowych.|
   |[Int32](/dotnet/api/system.int32)|Reprezentuje całkowita 32-bitowych.|
   |[Int64](/dotnet/api/system.int64)|Reprezentuje całkowita 64-bitowych.|
   |[IntPtr](/dotnet/api/system.intptr)|Typ specyficzny dla platformy, który jest używany do reprezentowania wskaźnika lub uchwytu.|
   |[SByte](/dotnet/api/system.byte)|Reprezentuje całkowita 8-bitowych.|
   |[Single](/dotnet/api/system.single)|Reprezentuje liczbę zmiennoprzecinkową pojedynczej precyzji.|
   |[TimeSpan](/dotnet/api/system.timespan)|Reprezentuje przedział czasu.|
   |[UInt16](/dotnet/api/system.uint16)|Reprezentuje 16-bitowa liczba całkowita bez znaku.|
   |[UInt32](/dotnet/api/system.uint32)|Reprezentuje 32-bitowa liczba całkowita bez znaku.|
   |[UInt64 —](/dotnet/api/system.uint64)|Reprezentuje 64-bitowej nieoznaczonej liczby całkowitej.|
   |[UIntPtr](/dotnet/api/system.uintptr)|Typ specyficzny dla platformy, który jest używany do reprezentowania wskaźnika lub uchwytu.|
   |[Void](/dotnet/api/system.void)|Wskazuje metodę, która nie zwraca wartości; oznacza to, że metoda ma zwracać typ void.|