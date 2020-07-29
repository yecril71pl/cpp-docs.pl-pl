---
title: /clr Ograniczenia
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: 641e83cb85b6282e8c4c82dfed8c4b44fc4a7e8f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223905"
---
# <a name="clr-restrictions"></a>/clr Ograniczenia

Należy pamiętać o następujących ograniczeniach dotyczących używania **/CLR**:

- W programie obsługi wyjątków strukturalnych istnieją ograniczenia dotyczące używania `_alloca` kompilacji z **/CLR**. Aby uzyskać więcej informacji, zobacz [_alloca](../../c-runtime-library/reference/alloca.md).

- Użycie testów błędów w czasie wykonywania jest nieprawidłowe z **/CLR**. Aby uzyskać więcej informacji, zobacz [jak: korzystanie z natywnych testów w czasie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks).

- Gdy **/CLR** jest używany do kompilowania programu, który używa tylko standardowej składni języka C++, następujące wskazówki dotyczą użycia wbudowanego zestawu:

  - Wbudowany kod asemblera, który przyjmuje wiedzę na temat natywnego układu stosu, konwencji wywoływania poza bieżącą funkcję lub inne informacje niskiego poziomu dotyczące komputera mogą się nie powieść, jeśli ta wiedza zostanie zastosowana do ramki stosu dla funkcji zarządzanej. Funkcje zawierające kod asemblera wbudowanego są generowane jako funkcje niezarządzane, tak jakby były umieszczone w osobnym module, który został skompilowany bez **/CLR**.

  - Wbudowany kod asemblera w funkcjach, które nie są obsługiwane przez parametry funkcji skonstruowane przez kopiowanie.

- Nie można wywołać [funkcji vprintf —](../../c-runtime-library/vprintf-functions.md) z programu skompilowanego z **/CLR**.

- Modyfikator [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) owies jest ignorowany w obszarze/CLR.

- Funkcja translator ustawiona przez [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) będzie miała wpływ tylko na przechwytywanie w kodzie niezarządzanym. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../extensions/exception-handling-cpp-component-extensions.md) .

- Porównanie wskaźników funkcji jest niedozwolone w przypadku opcji **/CLR**.

- Użycie funkcji, które nie są w pełni prototypowe jest niedozwolone w przypadku opcji **/CLR**.

- Następujące opcje kompilatora nie są obsługiwane z **/CLR**:

  - **/EHsc** i **/EHS** (**/CLR** implikuje **/EHa** (patrz [/EH (model obsługi wyjątków)](eh-exception-handling-model.md))

  - **/FP: Strict** i **/FP: except** (patrz [/FP (Określanie zachowania zmiennoprzecinkowego)](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/GM](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- Kombinacja `_STATIC_CPPLIB` definicji preprocesora ( `/D_STATIC_CPPLIB` ) i opcji kompilatora **/CLR** nie jest obsługiwana. Jest tak dlatego, że definicja spowodowałaby połączenie aplikacji ze statyczną wielowątkową biblioteką języka C++, która nie jest obsługiwana. Aby uzyskać więcej informacji, zobacz temat [/MD,/MT,/LD (Use Run-Time Library)](md-mt-ld-use-run-time-library.md) .

- W przypadku korzystania z programu **/Zi** z **/CLR**istnieją konsekwencje związane z wydajnością. Aby uzyskać więcej informacji, zobacz [/Zi](z7-zi-zi-debug-information-format.md).

- Przekazywanie znaku dwubajtowego do procedury wyjściowej .NET Framework bez również określania [/Zc: wchar_t](zc-wchar-t-wchar-t-is-native-type.md) lub bez rzutowania znaku do **`__wchar_t`** spowoduje wyświetlenie danych wyjściowych jako `unsigned short int` . Na przykład:

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](gs-buffer-security-check.md) jest ignorowany podczas kompilowania z **/CLR**, chyba że funkcja jest `#pragma` [niezarządzana](../../preprocessor/managed-unmanaged.md) lub jeśli funkcja musi być skompilowana do natywnego, w takim przypadku kompilator generuje C4793 ostrzeżeń, który jest domyślnie wyłączony.

- Zobacz [/entry](entry-entry-point-symbol.md) , aby uzyskać wymagania dotyczące sygnatury funkcji aplikacji zarządzanej.

- Aplikacje skompilowane za pomocą **/OpenMP** i **/CLR** można uruchomić tylko w jednym procesie AppDomain.  Aby uzyskać więcej informacji, zobacz [/OpenMP (Włącz obsługę openmp 2,0)](openmp-enable-openmp-2-0-support.md) .

- Funkcje, które przyjmują zmienną liczbę argumentów (VarArgs), zostaną wygenerowane jako funkcje natywne. Wszystkie typy danych zarządzanych w pozycji argumentu zmienna będą przekazywane do typów natywnych. Należy zauważyć, że <xref:System.String?displayProperty=fullName> typy są ciągami znaków dwubajtowych, ale są one organizowane w postaci ciągów znaków jednostronicowych. Tak więc jeśli specyfikator printf to% S (wchar_t *), będzie on organizować ciąg% s zamiast.

- Przy użyciu makra va_arg, podczas kompilowania z **/CLR: Pure**mogą wystąpić nieoczekiwane wyniki. Aby uzyskać więcej informacji, zobacz [va_arg, va_copy, va_end va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). **/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nie są obsługiwane w programie Visual Studio 2017 lub nowszym. Kod, który musi mieć wartość "Pure" lub "Safe", należy przenieść do języka C#.

- Nie należy wywoływać, z kodu zarządzanego, wszystkich funkcji, które przeprowadzą stos w celu uzyskania informacji o parametrach (argumenty funkcji); warstwa P/Invoke powoduje, że te informacje powinny być bardziej przypadające na stosie.  Na przykład nie Kompiluj proxy/stub z **/CLR**.

- Funkcje będą kompilowane do kodu zarządzanego wszędzie tam, gdzie to możliwe, ale nie wszystkie konstrukcje C++ można przetłumaczyć na kod zarządzany.  To ustalenie jest wykonywane na zasadzie funkcji po funkcji. Jeśli jakakolwiek część funkcji nie może zostać przekonwertowana na kod zarządzany, cała funkcja zostanie przekonwertowana na kod natywny. Poniższe przypadki uniemożliwiają kompilatorowi generowanie kodu zarządzanego.

  - Wygenerowane przez kompilator funkcje sekcje thunk lub pomocnika. Natywne sekcje thunk są generowane dla każdego wywołania funkcji przez wskaźnik funkcji, w tym wywołania funkcji wirtualnych.

  - Funkcja, która wywołuje `setjmp` lub `longjmp` .

  - Funkcje, które używają pewnych procedur wewnętrznych do bezpośredniego manipulowania zasobami maszynowymi. Na przykład użycie funkcji `__enable` i `__disable` , `_ReturnAddress` i `_AddressOfReturnAddress` lub lub multimediów wewnętrznych spowoduje wszystkie wyniki w kodzie natywnym.

  - Funkcje, które są zgodne z `#pragma unmanaged` dyrektywą. (Należy zauważyć, że Funkcja odwrotna, `#pragma managed` również jest obsługiwana).

  - Funkcja, która zawiera odwołania do typów wyrównanych, czyli typów zadeklarowanych za pomocą `__declspec(align(...))` .

## <a name="see-also"></a>Zobacz także

- [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](clr-common-language-runtime-compilation.md)
