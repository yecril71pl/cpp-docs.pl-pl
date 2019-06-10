---
title: Konfigurowanie projektów systemu Linux, aby używać moduł czyszczący adresu
description: W tym artykule opisano sposób konfigurowania C++ projektów systemu Linux w programie Visual Studio, aby użyć moduł czyszczący adresu.
ms.date: 06/07/2019
ms.openlocfilehash: 2415e8971614de35f046b699ce99c3822faf9372
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66823572"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Konfigurowanie projektów systemu Linux, aby używać moduł czyszczący adresu

W programie Visual Studio 2019 r wersji 16.1 Obsługa AddressSanitizer (ASan) jest zintegrowana projektów systemu Linux. Można włączyć ASan dla projektów opartych na platformie MSBuild systemu Linux i projekty narzędzia CMake. Działa ona na zdalnych systemów Linux i podsystemu Windows dla systemu Linux (WSL).

## <a name="about-asan"></a>Temat ASan

ASan jest wykrywanie błędów pamięci środowiska uruchomieniowego, dla języka C /C++ który wychwytuje następujące błędy:

- Używany po zakończeniu bezpłatnego (delegujące wskaźnik odwołanie)
- Przepełnienie buforu sterty
- Przepełnienie bufora stosu
- Użyj po przywróceniu
- Użyj po zakresu
- Inicjowanie kolejności usterki

Gdy ASan wykryje błąd, go zatrzymuje wykonywanie natychmiast. Jeśli z włączoną funkcją ASan program zostanie uruchomiony w debugerze, zostanie wyświetlony komunikat, który opisuje typ błędu, adres pamięci oraz lokalizację w pliku źródłowym, w którym wystąpił błąd:

   ![Komunikat o błędzie ASan](media/asan-error.png)

W okienku debugowanie okna wyniki, można również wyświetlić pełne dane wyjściowe ASan (łącznie, gdzie uszkodzony pamięć została przydzielona/z cofniętą alokacją).

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>Włącz ASan dla projektów opartych na platformie MSBuild systemu Linux

Aby włączyć ASan dla projektów opartych na platformie MSBuild systemu Linux, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **właściwości**. Następnie przejdź do **właściwości konfiguracji** > **C /C++**  > **Sanitizers**. ASan jest włączone za pomocą kompilatora i konsolidatora flag i wymaga projektu do ponownej kompilacji do pracy.

![Włącz ASan dla projektu programu MSBuild](media/msbuild-asan-prop-page.png)

Flagi opcjonalne środowiska uruchomieniowego ASan można przekazać, przechodząc do **właściwości konfiguracji** > **debugowanie** > **AddressSanitizer środowiska uruchomieniowego flagi**. Kliknij strzałkę w dół, aby dodać lub usunąć flagi.

![Konfigurowanie ASan środowiska uruchomieniowego flagi](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Włącz ASan dla projektów programu Visual Studio narzędzia CMake

Aby włączyć ASan dla narzędzia CMake, kliknij prawym przyciskiem myszy pliku CMakeLists.txt w **Eksploratora rozwiązań** i wybierz polecenie **ustawienia narzędzia CMake dla projektu**.

Upewnij się, że konfiguracja systemu Linux (na przykład **debugowania dla systemu Linux**) wybranego w lewym okienku okna dialogowego:

![Konfiguracja debugowania systemu Linux](media/linux-debug-configuration.png)

W obszarze dostępne są następujące opcje ASan **ogólne**. Wprowadź ASan flagi środowiska uruchomieniowego w formacie "flagi = wartość", oddzielone średnikami.

![Konfiguracja debugowania systemu Linux](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>Zainstaluj ASan symbole debugowania

Aby włączyć diagnostykę ASan, należy zainstalować jego symboli debugowania (libasan dbg) na komputerze zdalnym systemem Linux lub WSL instalacji. Wersja dbg libasan, który należy załadować zależy od wersji kompilatora GCC zainstalowane na maszynie z systemem Linux:

|**Wersja ASan**|**Wersja kompilatora GCC**|
| --- | --- |
|libasan0|gcc-4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

Można określić wersji kompilatora GCC, możesz uzyskać, korzystając z tego polecenia:

```bash
gcc --version
```

Aby wyświetlić wersję dbg libasan, należy, uruchom program, a następnie sprawdź **debugowania** okienku **dane wyjściowe** okna. Wersja ASan, który jest ładowany odnosi się do wersji dbg libasan, potrzebne na maszynie z systemem Linux. Możesz użyć **Ctrl + F** "libasan" w oknie wyszukiwania. Jeśli masz libasan4, na przykład, zostanie wyświetlony wiersz, podobny do tego:

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

Usługa bits debugowania ASan można zainstalować na dystrybucje systemu Linux, używanego przez apt za pomocą następującego polecenia. To polecenie powoduje zainstalowanie wersji 4:

```bash
sudo apt-get install libasan4-dbg
```

Jeśli włączono ASan, Visual Studio wyświetli monit w górnej części **debugowania** okienku **dane wyjściowe** okna, aby zainstalować symbole debugowania ASan.
