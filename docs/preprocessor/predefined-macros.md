---
title: Wstępnie zdefiniowane makra
ms.custom: update_every_version
ms.date: 04/05/2019
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
- __func__
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- _ATL_VER macro
- __ATOM__ macro
- __AVX__ macro
- __AVX2__ macro
- _CHAR_UNSIGNED macro
- __CLR_VER macro
- _CONTROL_FLOW_GUARD macro
- __COUNTER__ macro
- __cplusplus macro
- __cplusplus_cli macro
- __cplusplus_winrt macro
- _CPPRTTI macro
- _CPPUNWIND macro
- __DATE__ macro
- _DEBUG macro
- _DLL macro
- __FILE__ macro
- __FUNCDNAME__ macro
- __FUNCSIG__ macro
- __FUNCTION__ macro
- _INTEGRAL_MAX_BITS macro
- _ISO_VOLATILE macro
- _KERNEL_MODE macro
- __LINE__ macro
- _M_AMD64 macro
- _M_ARM macro
- _M_ARM_ARMV7VE macro
- _M_ARM_FP macro
- _M_ARM64 macro
- _M_CEE macro
- _M_CEE_PURE macro
- _M_CEE_SAFE macro
- _M_FP_EXCEPT macro
- _M_FP_FAST macro
- _M_FP_PRECISE macro
- _M_FP_STRICT macro
- _M_IX86 macro
- _M_IX86_FP macro
- _M_X64 macro
- _MANAGED macro
- _MFC_VER macro
- _MSC_BUILD macro
- _MSC_EXTENSIONS macro
- _MSC_FULL_VER macro
- _MSC_VER macro
- _MSVC_LANG macro
- __MSVC_RUNTIME_CHECKS macro
- _MT macro
- _NATIVE_WCHAR_T_DEFINED macro
- _NO_SIZED_DEALLOCATION macro
- _OPENMP macro
- _PREFAST_ macro
- _RESUMABLE_FUNCTIONS_SUPPORTED macro
- _RTC_CONVERSION_CHECKS_ENABLED macro
- __STDC__ macro
- __STDC_HOSTED__ macro
- __STDCPP_THREADS__ macro
- __TIME__ macro
- __TIMESTAMP__ macro
- __VA_ARGS__ macro
- _VC_NODEFAULTLIB macro
- _WCHAR_T_DEFINED macro
- _WIN32 macro
- _WIN64 macro
- _WINRT_DLL macro
- __func__ identifier
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
ms.openlocfilehash: bf74bc3b5293cba018c07b6b5c56c85695db7635
ms.sourcegitcommit: 6cb0670ca7d40e8ec55f162b8ce2847f5ae15f5c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67787367"
---
# <a name="predefined-macros"></a>Wstępnie zdefiniowane makra

Kompilator Microsoft C/C++ (MSVC) powoduje wstępne definiowanie pewne makra preprocesora, w zależności od języka (C lub C++), element docelowy kompilacji i opcje kompilatora wybrany.

MSVC obsługuje wstępnie zdefiniowane makra preprocesora, wymagane przez standard ANSI/ISO C99 i ISO C ++ 14 i C ++ 17 standardy. Implementacja obsługuje również kilka więcej makra preprocesora specyficzne dla firmy Microsoft. Niektóre makra są zdefiniowane tylko dla środowisk konkretnej kompilacji lub opcji kompilatora. Z wyjątkiem w przypadku, gdy zaznaczono inaczej, makra są zdefiniowane w całej jednostki translacji, tak, jakby zostały określone w postaci **/D** argumentach opcji kompilatora. Po zdefiniowaniu makra rozwijane do określonej wartości przez preprocesor przed kompilacją. Wstępnie zdefiniowane makra nie przyjmują argumentów i nie mogą zostać redefiniowane.

## <a name="standard-predefined-identifier"></a>Standardowa predefiniowany identyfikator

Kompilator obsługuje ten predefiniowany identyfikator określony przez ISO C99 i ISO C ++ 11.

- **&#95;&#95;FUNC&#95; &#95;**  niekwalifikowaną i unadorned nazwę otaczającej funkcji jako funkcja local **statyczna stała** tablicę **char**.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Standardowa wstępnie zdefiniowane makra

Te wstępnie zdefiniowane makra, określonego przez ISO C99 i C ++ 17 standardów ISO obsługiwanych przez kompilator.

- **&#95;&#95;cplusplus** zdefiniowany jako literał liczby całkowitej, podczas kompilowania jednostki translacji, co kod C++. W przeciwnym razie jest niezdefiniowany.

- **&#95;&#95;Data&#95; &#95;**  Data kompilacji bieżącego pliku źródłowego. Data jest ciągiem o stałej długości literału formularza *Mmm dd rrrr*. Nazwa miesiąca *Mmm* jest taka sama jak skrócona nazwa miesiąca wygenerowany przez bibliotekę środowiska uruchomieniowego C (CRT) [asctime —](../c-runtime-library/reference/asctime-wasctime.md) funkcji. Pierwszy znak data *dd* to miejsce, jeśli wartość jest mniejsza niż 10. To makro, zawsze jest definiowany.

- **&#95;&#95;PLIK&#95; &#95;**  nazwa bieżącego pliku źródłowego. **&#95;&#95;PLIK&#95; &#95;**  rozwija do literału ciągu znaków. Aby upewnić się, że pełna ścieżka do pliku jest wyświetlany, należy użyć [/FC (pełna ścieżka z pliku kodu źródłowego w diagnostyce)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). To makro, zawsze jest definiowany.

- **&#95;&#95;WIERSZ&#95; &#95;**  zdefiniowany jako liczba całkowita numer wiersza w bieżącym pliku źródłowym. Wartość **&#95; &#95;wiersza&#95; &#95;** makra można zmienić za pomocą `#line` dyrektywy. To makro, zawsze jest definiowany.

- **&#95;&#95;STDC&#95; &#95;**  zdefiniowana jako 1, tylko wtedy, gdy kompilowany jako C, a jeśli [/Za](../build/reference/za-ze-disable-language-extensions.md) określono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;&#95;STDC&#95;HOSTOWANA&#95; &#95;**  zdefiniowana jako 1, jeśli implementacja jest *hostowanych implementacji*, taki, który obsługuje całe wymagane biblioteki standardowej. W przeciwnym razie jest zdefiniowana jako 0.

- **&#95;&#95;STDCPP&#95;WĄTKÓW&#95; &#95;**  zdefiniowana jako 1, tylko wtedy, gdy program może mieć więcej niż jeden wątek wykonywania i kompilowane jako języka C++. W przeciwnym razie jest niezdefiniowany.

- **&#95;&#95;CZAS&#95; &#95;**  podczas tłumaczenia jednostki translacji wstępnie przetworzony. Czas jest ciągiem znaków literału formularza *: mm: ss*, taki sam jak czas zwrócony przez CRT [asctime —](../c-runtime-library/reference/asctime-wasctime.md) funkcji. To makro, zawsze jest definiowany.

## <a name="microsoft-specific-predefined-macros"></a>Wstępnie zdefiniowane makra specyficzne dla firmy Microsoft

MSVC obsługuje te dodatkowe wstępnie zdefiniowanych makr.

- **&#95;&#95;ATOM&#95; &#95;**  zdefiniowana jako 1 gdy [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) ustawiono opcję kompilatora, a kompilator jest x86 lub x64. W przeciwnym razie jest niezdefiniowany.

- **&#95;&#95;AVX&#95; &#95;**  zdefiniowana jako 1 gdy [/arch:](../build/reference/arch-x86.md) lub [/arch:AVX2](../build/reference/arch-x86.md) opcje kompilatora są ustawiane i kompilator jest x86 lub x64. W przeciwnym razie jest niezdefiniowany.

- **&#95;&#95;AVX2&#95; &#95;**  zdefiniowana jako 1 gdy [/arch:AVX2](../build/reference/arch-x86.md) ustawiono opcję kompilatora, a kompilator jest x86 lub x64. W przeciwnym razie jest niezdefiniowany.

- **&#95;CHAR&#95;bez znaku** zdefiniowana jako 1, jeśli wartość domyślna **char** typu jest niepodpisany. Ta wartość jest definiowana po [/J (domyślny typ unsigned char)](../build/reference/j-default-char-type-is-unsigned.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;&#95;CLR&#95;VER** zdefiniowany jako literał liczby całkowitej, reprezentujący wersję z środowiska uruchomieniowego języka wspólnego (CLR) używane do kompilowania aplikacji. Wartość jest zakodowana w postaci `Mmmbbbbb`, gdzie `M` jest główną wersją środowiska uruchomieniowego, `mm` jest wersją pomocniczą środowiska uruchomieniowego, a `bbbbb` jest numerem kompilacji. **&#95;&#95;CLR&#95;VER** jest definiowany, jeśli [/CLR](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;KONTROLKA&#95;przepływu&#95;je przed NIEPRZEWIDZIANYMI** zdefiniowana jako 1 gdy [/GUARD: CF (Włącz ochronę przepływu sterowania)](../build/reference/guard-enable-control-flow-guard.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;&#95;Licznik&#95; &#95;**  Expands do literału typu integer, który zaczyna się od 0. Wartość jest zwiększana o 1 za każdym razem, gdy jest używany w pliku źródłowym lub uwzględniony w nagłówkach pliku źródłowego w. **&#95;&#95;Licznik&#95; &#95;**  pamięta jego stan, korzystając z wstępnie skompilowanych nagłówków. To makro, zawsze jest definiowany.

  W tym przykładzie użyto `__COUNTER__` do przypisywania unikatowych identyfikatorów dla trzech różnych obiektów tego samego typu. `exampleClass` Konstruktor przyjmuje liczbę całkowitą jako parametr. W `main`, aplikacja deklaruje trzy obiekty typu `exampleClass`przy użyciu `__COUNTER__` jako unikatowego parametru identyfikatora:

    ```cpp
    // macro__COUNTER__.cpp
    // Demonstration of __COUNTER__, assigns unique identifiers to
    // different objects of the same type.
    // Compile by using: cl /EHsc /W4 macro__COUNTER__.cpp
    #include <stdio.h>

    class exampleClass {
        int m_nID;
    public:
        // initialize object with a read-only unique ID
        exampleClass(int nID) : m_nID(nID) {}
        int GetID(void) { return m_nID; }
    };

    int main()
    {
        // __COUNTER__ is initially defined as 0
        exampleClass e1(__COUNTER__);

        // On the second reference, __COUNTER__ is now defined as 1
        exampleClass e2(__COUNTER__);

        // __COUNTER__ is now defined as 2
        exampleClass e3(__COUNTER__);

        printf("e1 ID: %i\n", e1.GetID());
        printf("e2 ID: %i\n", e2.GetID());
        printf("e3 ID: %i\n", e3.GetID());

        // Output
        // ------------------------------
        // e1 ID: 0
        // e2 ID: 1
        // e3 ID: 2

        return 0;
    }
    ```

- **&#95;&#95;cplusplus&#95;interfejsu wiersza polecenia** zdefiniowany jako liczby całkowitej wartość literału 200406 podczas kompilowania co kod C++ i [/CLR](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany. Po zdefiniowaniu  **&#95; &#95;cplusplus&#95;interfejsu wiersza polecenia** obowiązuje jednostkę tłumaczeniową.

    ```cpp
    // cplusplus_cli.cpp
    // compile by using /clr
    #include "stdio.h"
    int main() {
       #ifdef __cplusplus_cli
          printf("%d\n", __cplusplus_cli);
       #else
          printf("not defined\n");
       #endif
    }
    ```

- **&#95;&#95;cplusplus&#95;winrt** zdefiniowany jako liczby całkowitej wartość literału 201009 podczas kompilowania co kod C++ i [/ZW (kompilacja środowiska uruchomieniowego Windows)](../build/reference/zw-windows-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;CPPRTTI** zdefiniowana jako 1, jeśli [/GR (Włącz Run-Time informacje o typie)](../build/reference/gr-enable-run-time-type-information.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;CPPUNWIND** zdefiniowana jako 1, jeśli co najmniej jeden [/GX (Włącz obsługę wyjątków)](../build/reference/gx-enable-exception-handling.md), [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md), lub [/EH (Obsługa Model wyjątków)](../build/reference/eh-exception-handling-model.md) opcje kompilatora są ustawione. W przeciwnym razie jest niezdefiniowany.

- **&#95;DEBUGOWANIE** zdefiniowana jako 1 gdy [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [/mdd](../build/reference/md-mt-ld-use-run-time-library.md), lub [/mtd](../build/reference/md-mt-ld-use-run-time-library.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;Biblioteka DLL** zdefiniowana jako 1 gdy [/MD](../build/reference/md-mt-ld-use-run-time-library.md) lub [/mdd](../build/reference/md-mt-ld-use-run-time-library.md) — opcja kompilatora (wielowątkowe DLL) jest ustawiona. W przeciwnym razie jest niezdefiniowany.

- **&#95;&#95;FUNCDNAME&#95; &#95;**  definiowany jako ciąg literału zawierającego [nazwy ozdobionej](../build/reference/decorated-names.md) funkcji otaczającej. Makro jest zdefiniowany tylko w obrębie funkcji. **&#95; &#95;FUNCDNAME&#95; &#95;** makr nie jest rozwinięty, jeśli używasz [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) lub [/P](../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora.

   W tym przykładzie użyto `__FUNCDNAME__`, `__FUNCSIG__`, i `__FUNCTION__` makra, aby wyświetlić informacje o funkcji.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95;&#95;FUNCSIG&#95; &#95;**  definiowany jako ciąg literału zawierającego podpis funkcji otaczającej. Makro jest zdefiniowany tylko w obrębie funkcji. **&#95; &#95;FUNCSIG&#95; &#95;** makr nie jest rozwinięty, jeśli używasz [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) lub [/P](../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora. Podczas kompilowania elementu docelowego 64-bitowy, to Konwencja wywoływania `__cdecl` domyślnie. Na przykład użycie zobacz `__FUNCDNAME__` makra.

- **&#95;&#95;Funkcja&#95; &#95;**  definiowany jako ciąg literału zawierającego nieozdobioną nazwę funkcji otaczającej. Makro jest zdefiniowany tylko w obrębie funkcji. **&#95; &#95;Funkcja&#95; &#95;** makr nie jest rozwinięty, jeśli używasz [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) lub [/P](../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora. Na przykład użycie zobacz `__FUNCDNAME__` makra.

- **&#95;CAŁKOWITE&#95;MAX&#95;BITÓW** zdefiniowane jako liczba całkowita 64 wartości literału, maksymalny rozmiar (w bitach) dla typu całkowitego-wektor. To makro, zawsze jest definiowany.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95;&#95;Funkcja INTELLISENSE&#95; &#95;**  zdefiniowana jako 1 podczas kompilatora IntelliSense przekazać w środowisku IDE programu Visual Studio. W przeciwnym razie jest niezdefiniowany. To makro umożliwia je przed nieprzewidzianymi kod kompilatora funkcji IntelliSense nie zrozumieć lub umożliwia przełączanie się między kompilacji i kompilatora IntelliSense. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z porady dotyczące powolność IntelliSense](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/).

- **&#95;ISO&#95;VOLATILE** zdefiniowana jako 1, jeśli [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;JĄDRA&#95;tryb** zdefiniowana jako 1, jeśli [/Kernel (Utwórz plik binarny trybu jądra)](../build/reference/kernel-create-kernel-mode-binary.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;AMD64** zdefiniowany jako literał liczby całkowitej wartość 100 kompilacje tej docelowej x64 procesorów. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;ARM** zdefiniowane jako liczby całkowitej wartość literału 7 dla kompilacji przeznaczonych dla procesorów ARM. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;ARM&#95;ARMV7VE** zdefiniowana jako 1 gdy [/arch:ARMv7VE](../build/reference/arch-arm.md) — opcja kompilatora jest ustawiona dla kompilacji przeznaczonych dla procesorów ARM. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;ARM&#95;FP** zdefiniowany jako literał wartość całkowitą, która wskazuje, które [/arch](../build/reference/arch-arm.md) — opcja kompilatora została ustawiona dla celów procesora ARM. W przeciwnym razie jest niezdefiniowany.

  - Wartość z zakresu od 30-39, jeśli nie `/arch` określono opcję ARM, wskazując architektura domyślne dla ARM ustawiono (`VFPv3`).

  - A wartość w zakresie 40-49 Jeśli `/arch:VFPv4` została ustawiona.

  - Aby uzyskać więcej informacji, zobacz [/arch (ARM)](../build/reference/arch-arm.md).

- **&#95;M&#95;ARM64** zdefiniowana jako 1 dla kompilacji przeznaczonych dla 64-bitowych procesorach ARM. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;CEE** zdefiniowane jako 001 Jeśli dowolny [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;CEE&#95;CZYSTEJ** przestarzałe począwszy od wersji programu Visual Studio 2015. Zdefiniowane jako 001 Jeśli [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;CEE&#95;bezpieczne** przestarzałe począwszy od wersji programu Visual Studio 2015. Zdefiniowane jako 001 Jeśli [/CLR: Safe](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;FP&#95;EXCEPT** zdefiniowana jako 1, jeśli [/FP: except](../build/reference/fp-specify-floating-point-behavior.md) lub [/FP: strict](../build/reference/fp-specify-floating-point-behavior.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;FP&#95;szybkie** zdefiniowana jako 1, jeśli [Fast](../build/reference/fp-specify-floating-point-behavior.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;FP&#95;PRECISE** zdefiniowana jako 1, jeśli [/FP: precise](../build/reference/fp-specify-floating-point-behavior.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;FP&#95;STRICT** zdefiniowana jako 1, jeśli [/FP: strict](../build/reference/fp-specify-floating-point-behavior.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;M&#95;IX86** zdefiniowany jako literał liczby całkowitej wartości 600 dla kompilacji tej docelowej x86 procesorów. To makro nie jest zdefiniowany dla x64 lub obiekty docelowe kompilacji ARM.

- **&#95;M&#95;IX86&#95;FP** zdefiniowany jako literał wartość całkowitą, która wskazuje [/arch](../build/reference/arch-arm.md) opcję kompilatora, który był zestaw lub wartość domyślną. To makro jest definiowane zawsze, gdy element docelowy kompilacji jest x86 procesora. W przeciwnym razie jest niezdefiniowany. Po zdefiniowaniu wartość to:

  - 0, jeśli `/arch:IA32` ustawiono opcję kompilatora.

  - 1, jeśli `/arch:SSE` ustawiono opcję kompilatora.

  - 2, jeśli `/arch:SSE2`, `/arch:AVX`, lub `/arch:AVX2` ustawiono opcję kompilatora. Ta wartość jest domyślna Jeżeli `/arch` nie określono opcję kompilatora. Gdy `/arch:AVX` jest określony, makro **&#95; &#95;AVX&#95; &#95;** jest również definiowany. Gdy `/arch:AVX2` jest określony, zarówno **&#95; &#95;AVX&#95; &#95;** i **&#95; &#95;AVX2&#95; &#95;** również są zdefiniowane.

  - Aby uzyskać więcej informacji, zobacz [/arch (x86)](../build/reference/arch-x86.md).

- **&#95;M&#95;X64** zdefiniowany jako literał liczby całkowitej wartość 100 kompilacje tej docelowej x64 procesorów. W przeciwnym razie jest niezdefiniowany.

- **&#95;ZARZĄDZANE** zdefiniowana jako 1 gdy [/CLR](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;MSC&#95;kompilacji** zdefiniowany jako literał liczby całkowitej zawierający element numer poprawki numeru wersji kompilatora. Numer wersji jest czwartym elementem numer wersji rozdzielanego kropką. Na przykład, jeśli numer wersji kompilatora firmy Microsoft C/C++ to 15.00.20706.01  **&#95;MSC&#95;kompilacji** — makro daje w wyniku 1. To makro, zawsze jest definiowany.

- **&#95;MSC&#95;rozszerzenia** zdefiniowana jako 1, jeśli na domyślnie [/Ze (Włącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;MSC&#95;pełne&#95;VER** zdefiniowane jako literał liczby całkowitej kodująca głównej, pomocnicza i Utwórz numer elementy numeru wersji kompilatora. Numer główny to pierwszy element numer wersji rozdzielanego kropką, numer podrzędny to drugi element i numer kompilacji to trzeci element. Na przykład, jeśli numer wersji kompilatora firmy Microsoft C/C++ to 15.00.20706.01  **&#95;MSC&#95;pełne&#95;VER** — makro daje w wyniku 150020706. Wprowadź `cl /?` w wierszu polecenia, aby wyświetlić numer wersji kompilatora. To makro, zawsze jest definiowany.

- **&#95;MSC&#95;VER** zdefiniowany jako literał liczby całkowitej kodująca głównych i pomocniczych numerów elementów numeru wersji kompilatora. Numer główny to pierwszy element numer wersji rozdzielanego kropką, a numer podrzędny to drugi element. Na przykład, jeśli numer wersji kompilatora firmy Microsoft C/C++ to 17.00.51106.1  **&#95;MSC&#95;VER** — makro daje w wyniku 1700. Wprowadź `cl /?` w wierszu polecenia, aby wyświetlić numer wersji kompilatora. To makro, zawsze jest definiowany.

   |Wersja programu Visual Studio|**&#95;MSC&#95;VER**|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 (7.0)|1300|
   |Visual Studio .NET 2003 (7.1)|1310|
   |Visual Studio 2005 (8.0)|1400|
   |Visual Studio 2008 (9.0)|1500|
   |Visual Studio 2010 (10.0)|1600|
   |Visual Studio 2012 (11.0)|1700|
   |Visual Studio 2013 (12.0)|1800|
   |Visual Studio 2015 (14.0)|1900|
   |Visual Studio 2017 RTW (15.0)|1910|
   |Visual Studio 2017 w wersji 15.3|1911|
   |Visual Studio 2017 w wersji 15.5|1912|
   |Visual Studio 2017 wersja 15.6|1913|
   |Visual Studio 2017 w wersji 15.7|1914|
   |Visual Studio 2017 w wersji 15.8|1915|
   |Visual Studio 2017 w wersji 15.9|1916|
   |Visual Studio 2019 RTW (16.0)|1920|
   |Visual Studio 2019 wersji 16.1|1921|
   |Visual Studio 2019 wersji 16.2|1922|
   |Visual Studio 2019 wersji 16.3|1923|

   Aby sprawdzić wersje kompilatora lub w danej wersji programu Visual Studio lub po aktualizacji, użyj **>=** operatora. W dyrektywie warunkowy służy do porównywania  **&#95;MSC&#95;VER** względem tego znaną wersją. Jeśli masz kilka wersji wzajemnie wykluczających się do porównywania, kolejności porównywania malejąco według numeru wersji. Na przykład ten kod wyszukuje kompilatory ogólnie dostępnych w programie Visual Studio 2017 i nowszych wersjach. Następnie sprawdza kompilatory wydane w lub po programu Visual Studio 2015. Następnie sprawdza wszystkie kompilatory wydanych przed Visual Studio 2015:

   ```cpp
   #if _MSC_VER >= 1910
   // . . .
   #elif _MSC_VER >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   Aby uzyskać więcej informacji, zobacz [Visual C++ w wersji kompilatora](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) w blogu zespołu programu Microsoft C++.

- **&#95;MSVC&#95;LANG** zdefiniowany jako literał liczby całkowitej, która określa standard języka C++, które są objęte kompilator. Jest ustawiona tylko w kodzie skompilowanym co kod C++. Makro jest literał liczby całkowitej wartość 201402L domyślnie lub jeśli [/STD: c ++ 14](../build/reference/std-specify-language-standard-version.md) określono opcję kompilatora. Jeśli makro jest ustawiona wartość 201703L [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md) określono opcję kompilatora. Jest ustawiona na wartość nowszej, który jest nieokreślony podczas [/STD: c ++ najnowsze](../build/reference/std-specify-language-standard-version.md) określono opcję. W przeciwnym razie makro jest niezdefiniowane. **&#95;MSVC&#95;LANG** — makro i [/STD (Określ wersję standardu języka)](../build/reference/std-specify-language-standard-version.md) opcje kompilatora są dostępne począwszy od wersji programu Visual Studio 2015 Update 3.

- **&#95;&#95;MSVC&#95;środowiska URUCHOMIENIOWEGO&#95;SPRAWDZA** zdefiniowana jako 1, gdy dla jednego z [usunęliśmy](../build/reference/rtc-run-time-error-checks.md) ustawiono opcje kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;MT** zdefiniowana jako 1 gdy [/MD lub/mdd](../build/reference/md-mt-ld-use-run-time-library.md) (wielowątkowe DLL) lub [/MT lub/mtd](../build/reference/md-mt-ld-use-run-time-library.md) (wielowątkowe) jest określony. W przeciwnym razie jest niezdefiniowany.

- **&#95;NATYWNE&#95;WCHAR&#95;T&#95;zdefiniowane** zdefiniowana jako 1 gdy [/Zc:](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;OPENMP** zdefiniowane jako liczba całkowita 200203 literału, jeśli [/OpenMP (Włącz obsługę OpenMP 2.0)](../build/reference/openmp-enable-openmp-2-0-support.md) ustawiono opcję kompilatora. Ta wartość reprezentuje datę specyfikacji OpenMP implementowany przez MSVC. W przeciwnym razie jest niezdefiniowany.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREFAST&#95;**  zdefiniowana jako 1 gdy [/ analyze](../build/reference/analyze-code-analysis.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;&#95;Sygnatura CZASOWA&#95; &#95;**  definiowany jako ciąg literału zawierającego datę i godzinę ostatniej modyfikacji bieżącego pliku źródłowego w formie skróconej, stała długość zwróconych przez CRT [asctime —](../c-runtime-library/reference/asctime-wasctime.md) działanie, na przykład `Fri 19 Aug 13:32:58 2016`. To makro, zawsze jest definiowany.

- **&#95;VC&#95;NODEFAULTLIB** zdefiniowana jako 1 gdy [/Zl (Pomiń domyślną nazwę biblioteki)](../build/reference/zl-omit-default-library-name.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowany.

- **&#95;WCHAR&#95;T&#95;zdefiniowane** zdefiniowana jako 1 gdy domyślnie [/Zc:](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) ustawiono opcję kompilatora. **&#95;WCHAR&#95;T&#95;zdefiniowane** — makro jest zdefiniowany, ale jeśli nie ma wartości `/Zc:wchar_t-` — opcja kompilatora jest ustawiona, i **wchar_t** jest zdefiniowana w systemowym pliku nagłówkowym, objęte usługi Projekt. W przeciwnym razie jest niezdefiniowany.

- **&#95;Win32** zdefiniowane jako 1, gdy element docelowy kompilacji jest ARM 32-bitowych, ARM 64-bitowych x86, lub x 64. W przeciwnym razie jest niezdefiniowany.

- **&#95;Win64** zdefiniowana jako 1, jeśli element docelowy kompilacji jest 64-bitowych ARM lub x64. W przeciwnym razie jest niezdefiniowany.

- **&#95;WINRT&#95;DLL** zdefiniowana jako 1 gdy kompilowany jako języka C++, a oba [/ZW (kompilacja środowiska uruchomieniowego Windows)](../build/reference/zw-windows-runtime-compilation.md) i [/LD lub /LDd](../build/reference/md-mt-ld-use-run-time-library.md) opcje kompilatora są ustawione. W przeciwnym razie jest niezdefiniowany.

Nie makra preprocesora, które identyfikują wersji biblioteki ATL lub MFC są wstępnie zdefiniowane przez kompilator. ATL i MFC nagłówków biblioteki zdefiniować te makra wersji wewnętrznie. Są one niezdefiniowana w dyrektywy preprocesora dokonane przed wymagany nagłówek jest dołączony.

- **&#95;ATL&#95;VER** zdefiniowane w \<atldef.h > jako literał liczby całkowitej kodująca ATL numer wersji.

- **&#95;MFC&#95;VER** zdefiniowane w \<afxver_.h > jako literał liczby całkowitej kodująca numerem wersji MFC.

## <a name="see-also"></a>Zobacz także

[Makra (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[Operatory preprocesora](../preprocessor/preprocessor-operators.md)<br/>
[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)