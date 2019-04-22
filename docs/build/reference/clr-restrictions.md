---
title: /clr Ograniczenia
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: 21b7ead553871854c73021756eb2086f9e6e7393
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777821"
---
# <a name="clr-restrictions"></a>/clr Ograniczenia

Należy zauważyć następujące ograniczenia na użycie **/CLR**:

- W obsłudze wyjątków strukturalnych, istnieją ograniczenia dotyczące używania `_alloca` podczas kompilowania za pomocą **/CLR**. Aby uzyskać więcej informacji, zobacz [_alloca](../../c-runtime-library/reference/alloca.md).

- Użycie sprawdzanie błędów czasu wykonywania nie jest prawidłowa w przypadku **/CLR**. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z macierzystego sprawdzania w czasie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks).

- Gdy **/CLR** jest używany, aby skompilować program, który używa tylko standardową składnię C++, poniższe wskazówki dotyczą korzystania z wbudowanego asemblera:

  - Kod zestawu wbudowanego założono znajomość układ stosu macierzystego, konwencje poza bieżącą funkcję lub innych niskiego poziomu informacji o komputerze wywoływania może się niepowodzeniem, jeśli wiedzy stosowany do ramki stosu dla funkcji zarządzanych. Funkcje zawierające kod zestawu wbudowanego są generowane jako funkcji niezarządzanych, tak jakby były one umieszczone w oddzielny moduł, który został skompilowany bez **/CLR**.

  - Wbudowany kod asemblera w funkcje, które wychodzą parametrów funkcji skonstruowany kopiowania nie jest obsługiwana.

- [Vprintf — funkcje](../../c-runtime-library/vprintf-functions.md) nie można wywołać z programu, który został skompilowany przy użyciu **/CLR**.

- ["Naked"](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) modyfikator jest zignorowane z opcją/CLR.

- Funkcję tłumacza ustawione przez [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) wpłynie tylko połowy w niezarządzanym kodzie. Zobacz [wyjątków](../../extensions/exception-handling-cpp-component-extensions.md) Aby uzyskać więcej informacji.

- Porównanie wskaźników funkcji nie jest dozwolona w ramach **/CLR**.

- Korzystania z funkcji, które nie są w pełni prototypowane nie jest dozwolona w ramach **/CLR**.

- Następujące opcje kompilatora są nieobsługiwane w przypadku **/CLR**:

  - **/ EHsc** i **/EHS** (**/CLR** oznacza **/eha** (zobacz [/EH (Model obsługi wyjątku)](eh-exception-handling-model.md))

  - **/ FP: strict** i **/FP: except** (zobacz [/FP (określenie zachowania zmiennopozycyjna)](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- Kombinacja `_STATIC_CPPLIB` definicji preprocesora (`/D_STATIC_CPPLIB`) i **/CLR** — opcja kompilatora nie jest obsługiwana. Dzieje się tak dlatego definicji spowodowałoby aplikację, aby połączyć się przy użyciu statycznych wielowątkowe standardowej biblioteki C++, który nie jest obsługiwany. Aby uzyskać więcej informacji, zobacz [/ / MD, / MT, /LD (Korzystaj z bibliotek wykonawczych)](md-mt-ld-use-run-time-library.md) tematu.

- Korzystając z **/zi** z **/CLR**, ma to wpływ na wydajność. Aby uzyskać więcej informacji, zobacz [/zi](z7-zi-zi-debug-information-format.md).

- Przekazywanie znaków dwubajtowych do .NET Framework danych wyjściowych procedury bez jednoczesnego określenia [/Zc:](zc-wchar-t-wchar-t-is-native-type.md) lub bez rzutowania znak `__wchar_t` spowoduje, że dane wyjściowe są wyświetlane jako `unsigned short int`. Na przykład:

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/ GS](gs-buffer-security-check.md) jest ignorowany podczas kompilowania za pomocą **/CLR**, chyba że funkcja jest w obszarze `#pragma` [niezarządzanych](../../preprocessor/managed-unmanaged.md) lub jeśli funkcja musi zostać skompilowana do natywnego, w którym to przypadku kompilator wygeneruje Ostrzeżenie C4793, która jest domyślnie wyłączona.

- Zobacz [/Entry](entry-entry-point-symbol.md) wymagania podpisu funkcji zarządzanej aplikacji.

- Aplikacje skompilowane z **/OpenMP** i **/CLR** może być uruchamiany tylko w procesie pojedynczego elementu appdomain.  Zobacz [/OpenMP (Włącz obsługę OpenMP 2.0)](openmp-enable-openmp-2-0-support.md) Aby uzyskać więcej informacji.

- Funkcje, które przyjmują zmienną liczbę argumentów (VARARG) zostanie wygenerowany jako funkcje natywne. Wszystkie typy zarządzanych danych w miejscu zmiennych argumentów będzie można zorganizować typy natywne. Należy pamiętać, że <xref:System.String?displayProperty=fullName> typy są ciągami faktycznie znaków dwubajtowych, ale są one przekazywane do ciągów znaków jednobajtowych. Więc jeśli specyfikatora printf %S (wchar_t *), go będzie kierować ciąg %s zamiast tego.

- Korzystając z va_arg — makro, może uzyskać nieoczekiwane wyniki podczas kompilowania za pomocą **/CLR: pure**. Aby uzyskać więcej informacji, zobacz [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017. Kod, który musi być "czysta" lub "bezpieczne" powinny być przenoszone do C#.

- Nie należy wywołać, z kodu zarządzanego, wszystkie funkcje, które pomagają stosu, aby uzyskać informacje o parametrach (argumenty funkcji); Warstwa P/Invoke powoduje, że te informacje jako dalej na dół stosu.  Na przykład nie można skompilować proxy/zastępczego za pomocą **/CLR**.

- Funkcje, które będzie kompilowana do kodu zarządzanego, jeśli to możliwe, ale nie wszystkie konstrukcje C++ mogą być tłumaczone do kodu zarządzanego.  Jest wybierana na podstawie funkcji przez funkcję. Jeśli którejkolwiek funkcji nie można przekonwertować na kod zarządzany, całą funkcję zostaną przekonwertowane na kod natywny zamiast tego. Gdy uniemożliwić kompilatorowi generowanie kodu zarządzanego.

  - Generowane przez kompilator sekcje Thunk lub funkcji pomocnika. Sekcje Thunk natywne są generowane dla dowolnego wywołania funkcji za pomocą wskaźnika funkcji, łącznie z wywołania funkcji wirtualnej.

  - To wywołanie funkcji `setjmp` lub `longjmp`.

  - Funkcje, które umożliwia bezpośrednie manipulowanie zasoby maszyny niektóre procedury wewnętrzne. Na przykład użycie `__enable` i `__disable`, `_ReturnAddress` i `_AddressOfReturnAddress`, lub wewnętrznych elementów multimedialnych będą wszystkie wynik w kodzie natywnym.

  - Funkcje poniżej `#pragma unmanaged` dyrektywy. (Należy pamiętać, że odwrotność `#pragma managed`, jest również obsługiwany.)

  - Funkcja, która zawiera odwołania do wyrównanych typów, oznacza to, że typy zadeklarowane za pomocą `__declspec(align(...))`.

## <a name="see-also"></a>Zobacz także

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](clr-common-language-runtime-compilation.md)
