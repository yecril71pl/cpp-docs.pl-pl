---
title: Wstępnie zdefiniowane makra | Dokumentacja firmy Microsoft
ms.custom: update_every_version
ms.date: 04/30/2018
ms.technology:
- cpp-tools
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 692279d8c19f2a03dcd9388eb47a640dcb00658a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32425247"
---
# <a name="predefined-macros"></a>Wstępnie zdefiniowane makra

Kompilator Visual C++ powoduje wstępne definiowanie pewne makra preprocesora, w zależności od języka (C lub C++), element docelowy kompilacji i opcje kompilatora wybrany.

Visual C++ obsługuje wymagane wstępnie zdefiniowane makra preprocesora określony przez standardu ANSI/ISO C99 i ISO języka C ++ 14 standardowa. Implementacja obsługuje również kilka więcej makra preprocesora specyficzne dla firmy Microsoft. Niektóre makra są definiowane tylko w przypadku środowisk określonej kompilacji lub opcji kompilatora. O ile nie zaznaczono inaczej, makra są zdefiniowane w jednostce tłumaczenia, jakby zostały określone w postaci **/D** argumentów opcji kompilatora. Po zdefiniowaniu makra są rozwijane do określonych wartości przez preprocesora przed kompilacji. Wstępnie zdefiniowane makra nie przyjmują argumentów i nie można ponownie zdefiniować.

## <a name="standard-predefined-identifier"></a>Standardowy identyfikator wstępnie zdefiniowane

Kompilator obsługuje to wstępnie zdefiniowane identyfikator określony przez ISO C99 i ISO C ++ 11.

- **&#95;&#95;FUNC&#95; &#95;**  niekwalifikowanych i unadorned nazwę funkcji otaczającej jako funkcja lokalnego `static const` tablicę `char`.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Standardowe wstępnie zdefiniowane makra

Kompilator obsługuje te wstępnie zdefiniowane makra określony przez ISO C99 i C ++ 17 normy ISO.

- **&#95;&#95;cplusplus** zdefiniowany jako wartość literału, gdy jednostka tłumaczenia jest skompilowana jako C++. W przeciwnym razie jest niezdefiniowana.

- **&#95;&#95;Data&#95; &#95;**  Data kompilacji bieżącego pliku źródłowego. Data jest ciągiem o stałej długości w postaci literału *Mmm dd rrrr*. Ta nazwa *Mmm* jest taka sama jak nazwa skrócona miesiąca w dat generowane przez biblioteki C Runtime [asctime —](../c-runtime-library/reference/asctime-wasctime.md) funkcji. Pierwszy znak data *dd* jest spacją, jeśli wartość jest mniejsza niż 10. To makro zawsze jest definiowany.

- **&#95;&#95;PLIK&#95; &#95;**  nazwę bieżącego pliku źródłowego. **&#95;&#95;PLIK&#95; &#95;**  rozwijany do literału ciągu znaków. Aby upewnić się, że wyświetlana jest pełna ścieżka do pliku, należy użyć [/FC (pełna ścieżka z pliku kodu źródłowego w diagnostyce)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). To makro zawsze jest definiowany.

- **&#95;&#95;WIERSZ&#95; &#95;**  zdefiniowany jako liczba całkowita numer wiersza w bieżącym pliku źródłowego. Wartość **&#95; &#95;wiersza&#95; &#95;** makro można zmieniać za pomocą `#line` dyrektywy. To makro zawsze jest definiowany.

- **&#95;&#95;STDC&#95; &#95;**  zdefiniowany jako 1 tylko wtedy, gdy skompilowany, ponieważ C i jeśli [/Za](../build/reference/za-ze-disable-language-extensions.md) określono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;&#95;STDC&#95;HOSTOWANA&#95; &#95;**  zdefiniowany jako 1, jeśli implementacja jest *hostowanej implementacji*, obsługującą całe wymagane biblioteki standardowe. W przeciwnym razie jest zdefiniowana jako 0.

- **&#95;&#95;STDCPP&#95;WĄTKÓW&#95; &#95;**  zdefiniowany jako 1 tylko wtedy, gdy program może mieć więcej niż jeden wątek i skompilowany C++. W przeciwnym razie jest niezdefiniowana.

- **&#95;&#95;CZAS&#95; &#95;**  podczas tłumaczenia jednostki tłumaczenia wstępnie przetworzony. Czas jest ciągiem znaków w postaci literału *hh: mm:*, taki sam jak czas zwrócony przez biblioteki C Runtime [asctime —](../c-runtime-library/reference/asctime-wasctime.md) funkcji. To makro zawsze jest definiowany.

## <a name="microsoft-specific-predefined-macros"></a>Wstępnie zdefiniowane makra specyficzne dla firmy Microsoft

Microsoft Visual C++ obsługuje te dodatkowe wstępnie zdefiniowane makra.

- **&#95;&#95;ATOM&#95; &#95;**  zdefiniowany jako 1 w przypadku [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) — opcja kompilatora jest ustawiona, a element docelowy kompilatora jest x86 lub x64. W przeciwnym razie jest niezdefiniowana.

- **&#95;&#95;AVX&#95; &#95;**  zdefiniowany jako 1 w przypadku [/arch: avx](../build/reference/arch-x86.md) lub [/arch:AVX2](../build/reference/arch-x86.md) — opcje kompilatora są ustawiane i docelowy kompilatora jest x86 lub x64. W przeciwnym razie jest niezdefiniowana.

- **&#95;&#95;AVX2&#95; &#95;**  zdefiniowany jako 1 w przypadku [/arch:AVX2](../build/reference/arch-x86.md) — opcja kompilatora jest ustawiona, a element docelowy kompilatora jest x86 lub x64. W przeciwnym razie jest niezdefiniowana.

- **&#95;CHAR —&#95;niepodpisane** zdefiniowany jako 1, gdy domyślny `char` typu nie jest podpisany. To jest ustawiana w przypadku [/J (domyślny typ unsigned char)](../build/reference/j-default-char-type-is-unsigned.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;&#95;CLR&#95;VER** zdefiniowany jako literał całkowity, reprezentujący wersję środowiska CLR używany, gdy aplikacja została skompilowana. Wartość jest zakodowany w formie `Mmmbbbbb`, gdzie `M` jest główny numer wersji środowiska uruchomieniowego, `mm` jest podrzędny numer wersji środowiska uruchomieniowego, i `bbbbb` jest numer kompilacji. **&#95;&#95;CLR&#95;VER** jest zdefiniowana, jeśli [/CLR](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;FORMANT&#95;przepływ&#95;zabezpieczenia** zdefiniowany jako 1 w przypadku [/GUARD: CF (Włącz ochronę przepływu sterowania)](../build/reference/guard-enable-control-flow-guard.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;&#95;Licznik&#95; &#95;**  Expands na liczbę całkowitą literału, który rozpoczyna się od 0 i jest zwiększana o 1 za każdym razem, gdy jest on używany w pliku źródłowym lub częścią nagłówków pliku źródłowego. **&#95;&#95;Licznik&#95; &#95;**  są przechowywane dane stanu, gdy używasz prekompilowanych nagłówków. To makro zawsze jest definiowany.

  W tym przykładzie użyto `__COUNTER__` można przypisać do trzech różnych obiektów tego samego typu unikatowych identyfikatorów. `exampleClass` Konstruktor pobiera całkowitą jako parametr. W `main`, aplikacja deklaruje trzy obiekty typu `exampleClass`za pomocą `__COUNTER__` jako parametr unikatowy identyfikator:

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

- **&#95;&#95;cplusplus&#95;cli** zdefiniowany jako liczby całkowitej wartość literału 200406, gdy kompilowany jako C++ i [/CLR](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana. Po zdefiniowaniu  **&#95; &#95;cplusplus&#95;cli** jest włączona w jednostce tłumaczenia.

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

- **&#95;&#95;cplusplus&#95;winrt** zdefiniowany jako liczby całkowitej wartość literału 201009, gdy kompilowany jako C++ i [/ZW (kompilacja środowiska uruchomieniowego systemu Windows)](../build/reference/zw-windows-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;CPPRTTI** zdefiniowany jako 1, gdy [/GR (Włącz Run-Time informacji o typie)](../build/reference/gr-enable-run-time-type-information.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;CPPUNWIND** zdefiniowany jako 1, jeśli co najmniej jeden z [/GX (Włącz obsługę wyjątków)](../build/reference/gx-enable-exception-handling.md), [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md), lub [/EH (wyjątek obsługi modelu)](../build/reference/eh-exception-handling-model.md) są ustawione opcje kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;DEBUGOWANIE** zdefiniowany jako 1 w przypadku [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [/mdd](../build/reference/md-mt-ld-use-run-time-library.md), lub [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;Biblioteki DLL** zdefiniowany jako 1 w przypadku [/ / MD](../build/reference/md-mt-ld-use-run-time-library.md) lub [/mdd](../build/reference/md-mt-ld-use-run-time-library.md) ustawiono — opcja kompilatora (wielowątkowe biblioteki DLL). W przeciwnym razie jest niezdefiniowana.

- **&#95;&#95;FUNCDNAME&#95; &#95;**  zdefiniowany jako literału ciągu zawierający [dekorowane nazwy](../build/reference/decorated-names.md) funkcji otaczającej. Makro jest zdefiniowany tylko w obrębie funkcji. **&#95; &#95;FUNCDNAME&#95; &#95;** makro nie jest rozwinięty, jeśli używasz [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) lub [/P](../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora.

   W tym przykładzie użyto `__FUNCDNAME__`, `__FUNCSIG__`, i `__FUNCTION__` makra do wyświetlenia informacji o funkcji.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95;&#95;FUNCSIG&#95; &#95;**  zdefiniowany jako literału ciągu zawierający podpis funkcji otaczającej. Makro jest zdefiniowany tylko w obrębie funkcji. **&#95; &#95;FUNCSIG&#95; &#95;** makro nie jest rozwinięty, jeśli używasz [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) lub [/P](../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora. Podczas kompilacji elementu docelowego 64-bitowych, jest Konwencja wywoływania `__cdecl` domyślnie. Na przykład użycie zobacz `__FUNCDNAME__` makra.

- **&#95;&#95;Funkcja&#95; &#95;**  zdefiniowany jako literału ciągu zawierającego nazwę bez funkcji otaczającej. Makro jest zdefiniowany tylko w obrębie funkcji. **&#95; &#95;Funkcja&#95; &#95;** makro nie jest rozwinięty, jeśli używasz [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) lub [/P](../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora. Na przykład użycie zobacz `__FUNCDNAME__` makra.

- **&#95;CAŁKOWITE&#95;MAX&#95;BITÓW** zdefiniowane jako liczby całkowitej wartość literału 64, maksymalny rozmiar (w bitach)-vector typ całkowity. To makro zawsze jest definiowany.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95;&#95;INTELLISENSE&#95; &#95;**  zdefiniowany jako 1 podczas kompilatora IntelliSense należy przekazać w środowisku IDE programu Visual Studio. W przeciwnym razie jest niezdefiniowana. Można użyć tego makra chronią kodu kompilatora IntelliSense nie zrozumieć lub umożliwia przełączanie się między kompilacji i kompilatora IntelliSense. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z porady dotyczące powolność IntelliSense](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/).

- **&#95;ISO&#95;VOLATILE** zdefiniowany jako 1, gdy [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;JĄDRA&#95;tryb** zdefiniowany jako 1, gdy [/Kernel (Utwórz plik binarny trybu jądra)](../build/reference/kernel-create-kernel-mode-binary.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;AMD64** zdefiniowany jako literał liczby całkowitej wartość 100 dla kompilacji tego docelowego x64 procesorów. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;ARM** zdefiniowany jako liczby całkowitej wartość literału 7 dla kompilacji, które odnoszą się do procesorów ARM. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;ARM&#95;ARMV7VE** zdefiniowany jako 1 w przypadku [/arch:ARMv7VE](../build/reference/arch-arm.md) — opcja kompilatora jest ustawiony dla kompilacji, które odnoszą się do procesorów ARM. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;ARM&#95;FP** zdefiniowane jako wartość literału całkowitą, która wskazuje, które [/arch](../build/reference/arch-arm.md) — opcja kompilatora została ustawiona, jeśli element docelowy kompilacji jest procesor ARM. W przeciwnym razie jest niezdefiniowana.

  - W zakresie 30-39, jeśli nie **/arch** określono opcję ARM, wskazujący architektura domyślny dla ARM ustawiono (`VFPv3`).

  - W zakresie od 40-49, jeśli **/arch:VFPv4** została ustawiona.

  - Zobacz [/arch (ARM)](../build/reference/arch-arm.md) Aby uzyskać więcej informacji.

- **&#95;M&#95;ARM64** zdefiniowany jako 1 dla kompilacji przeznaczonych dla 64-bitowych procesorach ARM. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;CEE** zdefiniowane jako 001 Jeśli żadnego [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;CEE&#95;CZYSTEJ** przestarzałe począwszy od wersji programu Visual Studio 2015. Zdefiniowane jako 001 Jeśli [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;CEE&#95;bezpieczne** przestarzałe począwszy od wersji programu Visual Studio 2015. Zdefiniowane jako 001 Jeśli [/CLR: Safe](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;FP&#95;EXCEPT** zdefiniowany jako 1, gdy [/FP: except](../build/reference/fp-specify-floating-point-behavior.md) lub [/FP: strict](../build/reference/fp-specify-floating-point-behavior.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;FP&#95;FAST** zdefiniowany jako 1, gdy [Fast](../build/reference/fp-specify-floating-point-behavior.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;FP&#95;PRECISE** zdefiniowany jako 1, gdy [/FP: precise](../build/reference/fp-specify-floating-point-behavior.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;FP&#95;STRICT** zdefiniowany jako 1, gdy [/FP: strict](../build/reference/fp-specify-floating-point-behavior.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;M&#95;IX86** zdefiniowany jako literał liczby całkowitej wartość 600 dla kompilacji tego docelowego x86 procesorów. To makro nie jest zdefiniowany dla x64 lub obiekty docelowe kompilacji ARM.

- **&#95;M&#95;IX86&#95;FP** zdefiniowane jako wartość literału całkowitą, która wskazuje [/arch](../build/reference/arch-arm.md) opcję kompilatora, która została zestawu lub wartość domyślną. To makro zawsze jest definiowany podczas kompilowania elementu docelowego jest x86 procesora. W przeciwnym razie jest niezdefiniowana. Po zdefiniowaniu wartość to:

  - Jeśli 0 **/arch:IA32** ustawiono opcję kompilatora.

  - 1, gdy **/arch:SSE** ustawiono opcję kompilatora.

  - Jeśli 2 **SSE2**, **/arch: avx** lub **/arch:AVX2** ustawiono opcję kompilatora. Ta wartość jest wartością domyślną, jeśli **/arch** nie określono opcję kompilatora. Gdy **/arch: avx** jest określony, makro **&#95; &#95;AVX&#95; &#95;** jest także zdefiniowana. Gdy **/arch:AVX2** jest określony zarówno **&#95; &#95;AVX&#95; &#95;** i **&#95; &#95;AVX2&#95; &#95;** są również zdefiniowane.

  - Zobacz [/arch (x86)](../build/reference/arch-x86.md) Aby uzyskać więcej informacji.

- **&#95;M&#95;X64** zdefiniowany jako literał liczby całkowitej wartość 100 dla kompilacji tego docelowego x64 procesorów. W przeciwnym razie jest niezdefiniowana.

- **&#95;ZARZĄDZANE** zdefiniowany jako 1 w przypadku [/CLR](../build/reference/clr-common-language-runtime-compilation.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;MSC&#95;kompilacji** zdefiniowany jako literał całkowity, zawierającą numer wersji elementu numer wersji kompilatora. Numer wersji jest czwartym elementem numer wersji rozdzielaną kropkami. Na przykład, jeśli numer wersji kompilatora Visual C++ jest 15.00.20706.01  **&#95;MSC&#95;kompilacji** makro daje w wyniku 1. To makro zawsze jest definiowany.

- **&#95;MSC&#95;rozszerzenia** zdefiniowany jako 1, gdy [/Ze (Włącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) — opcja kompilatora jest ustawiona, co jest ustawieniem domyślnym. W przeciwnym razie jest niezdefiniowana.

- **&#95;MSC&#95;pełne&#95;VER** zdefiniowany jako literał całkowity, który koduje głównych, pomocnicze i kompilacji liczba elementów numer wersji kompilatora. Główny numer jest pierwszym elementem numer wersji rozdzielaną kropkami, numer pomocnicza jest drugi element i numer kompilacji jest trzeci element. Na przykład, jeśli numer wersji kompilatora Visual C++ jest 15.00.20706.01  **&#95;MSC&#95;pełne&#95;VER** makro daje w wyniku 150020706. Wprowadź **cl /?** w wierszu polecenia, aby wyświetlić numer wersji kompilatora. To makro zawsze jest definiowany.

- **&#95;MSC&#95;VER** zdefiniowany jako literał całkowity, który koduje główne i pomocnicze liczba elementów numer wersji kompilatora. Główny numer jest pierwszym elementem numer wersji rozdzielonym i numer pomocnicza jest drugiego elementu. Na przykład, jeśli numer wersji kompilatora Visual C++ jest 17.00.51106.1  **&#95;MSC&#95;VER** makro daje w wyniku 1700. Wprowadź **cl /?** w wierszu polecenia, aby wyświetlić numer wersji kompilatora. To makro zawsze jest definiowany.

   |Visual Studio w wersji|&AMP;#95;MSC&AMP;#95;VER|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 (7.0)|1300|
   |Visual Studio .NET 2003 (7.1)|1310|
   |Visual Studio 2005 (8.0)|1400|
   |Program Visual Studio 2008 (9.0)|1500|
   |Program Visual Studio 2010 (10.0)|1600|
   |Program Visual Studio 2012 (11.0)|1700|
   |Visual Studio 2013 (12.0)|1800|
   |Program Visual Studio 2015 (14.0)|1900|
   |RTW 2017 r w usłudze Visual Studio (15.0)|1910|
   |Visual Studio 2017 wersji 15 ustęp 3|1911|
   |Visual Studio 2017 wersji 15,5 cala|1912|
   |Visual Studio 2017 wersji 15,6|1913|
   |Visual Studio 2017 wersji 15.7|1914|

   Aby sprawdzić wersje kompilatora lub w danej wersji programu Visual Studio lub po aktualizacji, użyj **>=** operatora (większe lub równości), aby porównać  **&#95;MSC&#95;VER** przed którym wiadomo, że Wersja. Jeśli masz kilka wersji do porównania w sposób wykluczają się wzajemnie, firma Microsoft zaleca się, że kolejność porównywania według kolejności numer wersji. Na przykład ten kod sprawdza, czy kompilatory wydane w programie Visual Studio 2015 lub nowszego oraz kompilatory wydane w lub po Visual Studio 2013, podejmuje działanie dla wszystkich kompilatory wydanych przed Visual Studio 2013, a następnie:

   ```cpp
   #if _MSC_VER >= 1900
   // . . .
   #elif _MSC_VER >= 1800
   // . . .
   #else
   // . . .
   #endif
   ```

   Aby uzyskać więcej informacji, zobacz [kompilatora Visual C++ w wersji](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/) w blogu zespołu Visual C++.

- **&#95;MSVC&#95;LANG** zdefiniowany jako literał całkowity, który określa standard języka C++ docelowe przez kompilator. Skompilowany, ponieważ C++, makro jest liczbą całkowitą wartość literału 201402L Jeśli [/std:c ++ 14](../build/reference/std-specify-language-standard-version.md) — opcja kompilatora jest ustawiona lub domyślnie jest ustawiana na 201703 L Jeżeli [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md) ustawiono opcję kompilatora; i ma ustawioną wartość wyższy, nieokreślone wartość przy [/std:c ++ najnowsze](../build/reference/std-specify-language-standard-version.md). W przeciwnym razie makro jest niezdefiniowane. **&#95;MSVC&#95;LANG** makro i [/std (Określ wersję Standard języka)](../build/reference/std-specify-language-standard-version.md) — opcje kompilatora są dostępne począwszy od wersji programu Visual Studio 2015 Update 3.

- **&#95;&#95;MSVC&#95;środowiska URUCHOMIENIOWEGO&#95;SPRAWDZA** zdefiniowany jako 1, gdy dla jednego z [/RTC](../build/reference/rtc-run-time-error-checks.md) ustawiono opcje kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;MT** zdefiniowany jako 1 w przypadku [/ / MD lub/mdd](../build/reference/md-mt-ld-use-run-time-library.md) (wielowątkowe biblioteki DLL) lub [/MT lub /MTd](../build/reference/md-mt-ld-use-run-time-library.md) (Multithreaded) został określony. W przeciwnym razie jest niezdefiniowana.

- **&#95;NATYWNY&#95;WCHAR&#95;T&#95;zdefiniowane** zdefiniowany jako 1 w przypadku [/Zc:](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;OPENMP** zdefiniowany jako liczba całkowita 200203 literał reprezentujący datę specyfikacji OpenMP implementowane przez Visual C++, jeśli [/OpenMP (Włącz obsługę OpenMP 2.0)](../build/reference/openmp-enable-openmp-2-0-support.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREFAST&#95;**  zdefiniowany jako 1 w przypadku [/ analyze](../build/reference/analyze-code-analysis.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;&#95;Sygnatura CZASOWA&#95; &#95;**  zdefiniowany jako literału ciągu zawierający datę i godzinę ostatniej modyfikacji bieżącego pliku źródłowego w formie skróconej, stała długość zwróconych przez biblioteki C Runtime [asctime —](../c-runtime-library/reference/asctime-wasctime.md) funkcji, na przykład `Fri 19 Aug 13:32:58 2016`. To makro zawsze jest definiowany.

- **&#95;VC&#95;NODEFAULTLIB** zdefiniowany jako 1 w przypadku [/Zl (Pomiń domyślną nazwę biblioteki)](../build/reference/zl-omit-default-library-name.md) ustawiono opcję kompilatora. W przeciwnym razie jest niezdefiniowana.

- **&#95;WCHAR&#95;T&#95;zdefiniowane** zdefiniowany za 1, gdy domyślny [/Zc:](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) ustawiono opcję kompilatora. **&#95;WCHAR&#95;T&#95;zdefiniowane** makro jest zdefiniowany, ale nie ma wartości Jeśli **/Zc:wchar_t-** — opcja kompilatora jest ustawiona, i `wchar_t` jest zdefiniowany w pliku nagłówka systemu zawarte w projektu. W przeciwnym razie jest niezdefiniowana.

- **&#95;Win32** zdefiniowane jako element docelowy kompilacji jest 32-bitowych ARM ARM 64-bitowych x86, 1 lub x 64. W przeciwnym razie jest niezdefiniowana.

- **&#95;Win64** zdefiniowana jako 1, jeśli element docelowy kompilacji jest 64-bitowych ARM lub x64. W przeciwnym razie jest niezdefiniowana.

- **&#95;WINRT&#95;DLL** zdefiniowane jako 1 w przypadku skompilowany, ponieważ C++ i oba [/ZW (kompilacja środowiska uruchomieniowego systemu Windows)](../build/reference/zw-windows-runtime-compilation.md) i [/LD lub /LDd](../build/reference/md-mt-ld-use-run-time-library.md) są ustawione opcje kompilatora. W przeciwnym razie jest niezdefiniowana.

 Makra preprocesora, używane do określania wersji biblioteki ATL ani MFC nie są wstępnie zdefiniowane przez kompilator. Tych makr są definiowane w nagłówki biblioteki, dlatego są one niezdefiniowane dyrektywy preprocesora przed wymaganego nagłówka jest dołączony.

- **&#95;ATL&#95;VER** zdefiniowane w \<atldef.h > jako literał całkowity, który koduje ATL numer wersji.

- **&#95;MFC&#95;VER** zdefiniowane w \<afxver_.h > jako literał całkowity, który koduje numer wersji biblioteki MFC.

## <a name="see-also"></a>Zobacz też

[Makra (C/C++)](../preprocessor/macros-c-cpp.md)   
[Operatory preprocesora](../preprocessor/preprocessor-operators.md)   
[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)
