---
title: Konwertowanie projektów z trybu mieszanego na czysty język bezpośredni
ms.date: 08/19/2019
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 05ece23e6d79fc399085099deebcde0aa4a92c64
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630843"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Konwertowanie projektów z trybu mieszanego na czysty język pośredni

Wszystkie projekty C++ Visual CLR domyślnie łączą się z bibliotekami wykonawczymi C. W związku z tym projekty te są klasyfikowane jako aplikacje w trybie mieszanym, ponieważ łączą kod natywny z kodem, który jest przeznaczony dla środowiska uruchomieniowego języka wspólnego (kod zarządzany). Po skompilowaniu są one kompilowane w języku pośrednim (IL), znanym również jako język pośredni (MSIL) firmy Microsoft.

> [!IMPORTANT]
> Program Visual Studio 2015 jest przestarzały i program Visual Studio 2017 nie obsługuje już tworzenia opcji **/CLR: Pure** lub **/CLR: Safe** dla aplikacji CLR. Jeśli potrzebujesz czystych lub bezpiecznych zestawów, zalecamy przetłumaczenie aplikacji na C#.

Jeśli używasz wcześniejszej wersji zestawu narzędzi kompilatora firmy Microsoft C++ , który obsługuje **/CLR: Pure** lub **/CLR: Safe**, możesz użyć tej procedury, aby skonwertować kod na czysty MSIL:

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>Aby skonwertować aplikację w trybie mieszanym do czystego języka pośredniego

1. Usuń linki do [bibliotek środowiska uruchomieniowego C](../c-runtime-library/crt-library-features.md) (CRT):

   1. W pliku. cpp definiującym punkt wejścia aplikacji Zmień punkt wejścia na `Main()`. Użycie `Main()` wskazuje, że projekt nie łączy się z CRT.

   2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości** w menu skrótów, aby otworzyć strony właściwości aplikacji.

   3. Na stronie właściwości projektu zaawansowanego dla **konsolidatora**wybierz **punkt wejścia** , a następnie wprowadź wartość **Main** w tym polu.

   4. W przypadku aplikacji konsolowych na stronie właściwości projektu **systemu** dla **konsolidatora**wybierz pole **podsystem** i Zmień to na **Console (/SUBSYSTEM: Console)** .

      > [!NOTE]
      > Nie trzeba ustawiać tej właściwości dla Windows Forms aplikacji, ponieważ pole **podsystem** jest domyślnie ustawione na **system Windows (/SUBSYSTEM: Windows)** .

   5. W *stdafx. h*Dodaj komentarz do `#include` wszystkich instrukcji. Na przykład w aplikacjach konsoli programu:

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

   6. W przypadku aplikacji Windows Forms w formularzu Form1. cpp Dodaj komentarz do `#include` instrukcji odwołującej się do systemu Windows. h. Na przykład:

      ```cpp
      // #include <windows.h>
      ```

2. Dodaj następujący kod do *stdafx. h*:

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. Usuń wszystkie typy niezarządzane:

   Wszędzie tam, gdzie to konieczne, Zastąp typy niezarządzane odwołaniami do struktur z przestrzeni nazw [system](/dotnet/api/system) . Typy wspólne zarządzane są wymienione w poniższej tabeli:

   |Struktura|Opis|
   |---------------|-----------------|
   |[Boolean](/dotnet/api/system.boolean)|Reprezentuje wartość logiczną.|
   |[Byte](/dotnet/api/system.byte)|Reprezentuje 8-bitową liczbę całkowitą bez znaku.|
   |[Delikatn](/dotnet/api/system.char)|Reprezentuje znak Unicode.|
   |[DateTime](/dotnet/api/system.datetime)|Reprezentuje chwilę w czasie, zwykle wyrażoną jako datę i godzinę dnia.|
   |[Decimal](/dotnet/api/system.decimal)|Reprezentuje liczbę dziesiętną.|
   |[Double](/dotnet/api/system.double)|Reprezentuje liczbę zmiennoprzecinkową o podwójnej precyzji.|
   |[Ident](/dotnet/api/system.guid)|Reprezentuje unikatowy identyfikator globalny (GUID).|
   |[Int16](/dotnet/api/system.int16)|Reprezentuje 16-bitową liczbę całkowitą ze znakiem.|
   |[Int32](/dotnet/api/system.int32)|Reprezentuje 32-bitową liczbę całkowitą ze znakiem.|
   |[Int64](/dotnet/api/system.int64)|Reprezentuje 64-bitową liczbę całkowitą ze znakiem.|
   |[IntPtr](/dotnet/api/system.intptr)|Typ specyficzny dla platformy, który jest używany do reprezentowania wskaźnika lub dojścia.|
   |[SByte](/dotnet/api/system.byte)|Reprezentuje 8-bitową liczbę całkowitą ze znakiem.|
   |[Single](/dotnet/api/system.single)|Reprezentuje liczbę zmiennoprzecinkową o pojedynczej precyzji.|
   |[TimeSpan](/dotnet/api/system.timespan)|Reprezentuje interwał czasu.|
   |[UInt16](/dotnet/api/system.uint16)|Reprezentuje 16-bitową liczbę całkowitą bez znaku.|
   |[Równ](/dotnet/api/system.uint32)|Reprezentuje 32-bitową liczbę całkowitą bez znaku.|
   |[UInt64](/dotnet/api/system.uint64)|Reprezentuje 64-bitową liczbę całkowitą bez znaku.|
   |[UIntPtr](/dotnet/api/system.uintptr)|Typ specyficzny dla platformy, który jest używany do reprezentowania wskaźnika lub dojścia.|
   |[Pozycję](/dotnet/api/system.void)|Wskazuje metodę, która nie zwraca wartości; oznacza to, że metoda ma zwracany typ void.|