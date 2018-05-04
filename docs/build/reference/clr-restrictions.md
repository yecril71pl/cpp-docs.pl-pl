---
title: -clr ograniczenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 697e2a50e8c63928a52bd1d960dcdefad0fe87bb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="clr-restrictions"></a>/clr Ograniczenia
Należy zwrócić uwagę następujące ograniczenia dotyczące stosowania **/CLR**:  
  
-   W procedurze obsługi wyjątków strukturalnych, istnieją ograniczenia dotyczące używania `_alloca` podczas kompilowania za pomocą **/CLR**. Aby uzyskać więcej informacji, zobacz [_alloca](../../c-runtime-library/reference/alloca.md).  
  
-   Korzystanie z sprawdzanie błędów czasu wykonywania nie jest prawidłowy w przypadku **/CLR**. Aby uzyskać więcej informacji, zobacz [porady: Użyj natywnego Run-Time sprawdza](/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
-   Gdy **/CLR** jest używana do kompilowania program, który używa tylko standardowe składni języka C++, poniższe wskazówki dotyczą stosowania zestaw wbudowany:  
  
    -   Kod zestawu wbudowanego założono znajomość układu natywnego stosu, wywoływanie Konwencji poza bieżącą funkcję lub inne niskiego poziomu informacje o komputerze może się niepowodzeniem, jeśli wiedzy stosowany do ramki stosu funkcji zarządzanych. Funkcje zawierające kod zestawu wbudowanego są generowane jako niezarządzane funkcje, jak gdyby zostały one umieszczone w osobnym moduł, który został skompilowany bez **/CLR**.  
  
    -   Kod zestawu wbudowanego w funkcje, które przekazania parametrów funkcji skonstruowany kopiowania nie jest obsługiwane.  
  
-   [Vprintf — funkcje](../../c-runtime-library/vprintf-functions.md) nie można wywołać z poziomu programu skompilowane z **/CLR**.  
  
-   [Naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) modyfikator jest ignorowany w/CLR.  
  
-   Funkcja translator ustawione przez [_set_se_translator —](../../c-runtime-library/reference/set-se-translator.md) obejmie tylko połowy za pomocą kodu niezarządzanego. Zobacz [obsługi wyjątków](../../windows/exception-handling-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
-   Porównanie wskaźników funkcji jest niedozwolone w obszarze **/CLR**.  
  
-   Korzystanie z funkcji, które nie są w pełni prototypowanych nie jest dozwolone w obszarze **/CLR**.  
  
-   Następujące opcje kompilatora nie są obsługiwane przez **/CLR**:  
  
    -   **/ EHsc** i **/EHS** (**/CLR** oznacza **/eha** (zobacz [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md))  
  
    -   **/ FP: strict** i **/FP: except** (zobacz [/fp (określenie zachowania Floating-Point)](../../build/reference/fp-specify-floating-point-behavior.md))  
  
    -   [/Zd](../../build/reference/z7-zi-zi-debug-information-format.md)  
  
    -   [/Gm](../../build/reference/gm-enable-minimal-rebuild.md)  
  
    -   [/MT](../../build/reference/md-mt-ld-use-run-time-library.md)  
  
    -   [/RTC](../../build/reference/rtc-run-time-error-checks.md)  
  
    -   **/ZI**  
  
-   Kombinacja `_STATIC_CPPLIB` definicja preprocesora (`/D_STATIC_CPPLIB`) i **/CLR** — opcja kompilatora nie jest obsługiwana. Dzieje się tak dlatego definicji może spowodować, że aplikacja do łączenia z statycznych wielowątkowe standardowa biblioteka C++, która nie jest obsługiwana. Aby uzyskać więcej informacji, zobacz [/ / MD, / MT, /LD (Użyj biblioteki wykonawczej)](../../build/reference/md-mt-ld-use-run-time-library.md) tematu.  
  
-   Korzystając z **/zi** z **/CLR**, jest wpływ na wydajność. Aby uzyskać więcej informacji, zobacz [/zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
-   Przekazywanie znaków dwubajtowych .NET Framework output procedury bez określenia [/Zc:](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) lub bez rzutowania znak `__wchar_t` spowoduje, że dane wyjściowe do są wyświetlane jako `unsigned short int`. Na przykład:  
  
    ```  
    Console::WriteLine(L' ')              // Will output 32.  
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.  
    ```  
  
-   [/ GS](../../build/reference/gs-buffer-security-check.md) jest ignorowany podczas kompilowania za pomocą **/CLR**, chyba że funkcja podlega `#pragma` [niezarządzane](../../preprocessor/managed-unmanaged.md) lub jeśli funkcji muszą być skompilowane na natywny, w którym to przypadku kompilator generuje Ostrzeżenie C4793, który jest domyślnie wyłączone.  
  
-   Zobacz [/Entry](../../build/reference/entry-entry-point-symbol.md) wymagania podpisu funkcji zarządzanych aplikacji.  
  
-   Aplikacje skompilowane z **/OpenMP** i **/CLR** może być uruchamiany tylko w procesie pojedynczego elementu appdomain.  Zobacz [/OpenMP (Włącz obsługę OpenMP 2.0)](../../build/reference/openmp-enable-openmp-2-0-support.md) Aby uzyskać więcej informacji.  
  
-   Funkcje, których zmienną liczbę argumentów (VARARG) zostaną wygenerowane jako funkcje natywne. Wszystkie typy zarządzanych danych na pozycji zmiennych argumentów będzie można zorganizować natywnych typów. Należy pamiętać, że <xref:System.String?displayProperty=fullName> typy są faktycznie znaków dwubajtowych ciągów, ale są one przekazywane do ciągów znaków. Więc jeśli specyfikator printf %S (wchar_t *), go będzie kierować na ciąg %s zamiast tego.  
  
-   Korzystając z makra va_arg, mogą wystąpić nieoczekiwane wyniki podczas kompilowania za pomocą **/CLR: pure**.  Aby uzyskać więcej informacji, zobacz [va_arg, va_copy, va_end, va_start —](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md).  
  
-   Należy nie wywołać, z kodu zarządzanego, wszystkie funkcje, które opisano stos, aby uzyskać informacje o parametrach (argumenty funkcji); Warstwa P/Invoke powoduje, że te informacje będzie dalej w dół stosu.  Na przykład nie skompilować proxy/stub z **/CLR**.  
  
-   Funkcje zostanie skompilowany do kodu zarządzanego, jeśli to możliwe, ale nie wszystkie konstrukcje C++ mogą być przekonwertowana na stronę kodu zarządzanego.  Jest wybierana na podstawie funkcja przez funkcję. Jeśli dowolną część funkcji nie można przekonwertować na kod zarządzany, Cała funkcja zostanie przekonwertowany do kodu natywnego zamiast tego. Gdy zapobiec generowania kodu zarządzanego przez kompilator.  
  
    -   Generowane przez kompilator sekcje Thunk lub funkcje pomocnicze. Natywny sekcje Thunk są generowane dla każde wywołanie funkcji za pomocą wskaźnika funkcji, łącznie z wywołania funkcji wirtualnej.  
  
    -   Tego wywołania funkcji `setjmp` lub `longjmp`.  
  
    -   Funkcje, które umożliwiają niektórych wewnętrznej procedury bezpośrednio manipulowania zasoby maszyny. Na przykład użycie `__enable` i `__disable`, `_ReturnAddress` i `_AddressOfReturnAddress`, lub wszystkich wyników w kodzie natywnym zostanie funkcje wewnętrzne multimediów.  
  
    -   Funkcje poniżej `#pragma unmanaged` dyrektywy. (Należy pamiętać, że odwrotność, `#pragma managed`, jest również obsługiwany.)  
  
    -   Funkcja, która zawiera odwołania do wyrównane typy, oznacza to, że typy zadeklarowane za pomocą `__declspec(align(...))`.  
  
## <a name="see-also"></a>Zobacz też  
 [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)