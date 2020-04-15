---
title: Konfigurowanie projektów systemu Linux do używania narzędzia Address Sanitizer
description: W tym artykule opisano sposób konfigurowania projektów systemu Linux języka C++ w programie Visual Studio do używania funkcji dezynfekcji adresów.
ms.date: 06/07/2019
ms.openlocfilehash: 80e9ab46c948f2062391ae723c3425c435bd4507
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364312"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Konfigurowanie projektów systemu Linux do używania narzędzia Address Sanitizer

W programie Visual Studio 2019 w wersji 16.1 obsługa addresssanitizer (ASan) jest zintegrowana z projektami systemu Linux. Można włączyć ASan dla projektów opartych na systemie Linux opartych na systemie MSBuild i projektów CMake. Działa na zdalnych systemach Linux i w podsystemie Windows dla Linuksa (WSL).

## <a name="about-asan"></a>Więcej o: ASan

ASan jest detektorem błędów pamięci środowiska uruchomieniowego dla języka C/C++, który wykrywa następujące błędy:

- Użyj po wolnym (zwisające odniesienie do wskaźnika)
- Przepełnienie buforu sterty
- Przepełnienie buforu stosu
- Użyj po powrocie
- Użyj po zakresie
- Błędy kolejności inicjowania

Gdy ASan wykryje błąd, natychmiast zatrzymuje wykonywanie. Po uruchomieniu programu obsługującego technologię ASan w debugerze zostanie wyświetlony komunikat opisujący typ błędu, adres pamięci i lokalizację w pliku źródłowym, w której wystąpił błąd:

   ![Komunikat o błędzie ASan](media/asan-error.png)

Można również wyświetlić pełne dane wyjściowe ASan (w tym gdzie uszkodzona pamięć została przydzielona/cofnięta) w okienku debugowania okna wyjściowego.

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>Włączanie asanu dla projektów systemu Linux opartych na systemie MSBuild

> [!NOTE]
> Począwszy od programu Visual Studio 2019 w wersji 16.4, AddressSanitizer dla projektów systemu Linux jest włączona za pośrednictwem **właściwości** > konfiguracji**C/C++** > **Włącz dezynfekcji adresu**.

Aby włączyć ASan dla projektów opartych na systemie Linux opartych na systemie MSBuild, kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań** i wybierz polecenie **Właściwości**. Następnie przejdź do **właściwości konfiguracji** > **C/C++** > **Sanitizers**. ASan jest włączona za pośrednictwem flag kompilatora i konsolidatora i wymaga ponownego kompilacji projektu do pracy.

![Włączanie usługi ASan dla projektu MSBuild](media/msbuild-asan-prop-page.png)

Opcjonalne flagi środowiska uruchomieniowego ASan można przekazać, przechodząc do flag > środowiska wykonawczego Debugowania **adresów** > **debugowania.****AddressSanitizer Runtime Flags** Kliknij strzałkę w dół, aby dodać lub usunąć flagi.

![Konfigurowanie flag środowiska uruchomieniowego ASan](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Włączanie projektów ASan dla programu Visual Studio CMake

Aby włączyć ASan dla CMake, kliknij prawym przyciskiem myszy plik CMakeLists.txt w **Eksploratorze rozwiązań** i wybierz **pozycję CMake Settings for Project**.

Upewnij się, że w lewym okienku okna dialogowego wybrano konfigurację systemu Linux (na przykład **Linux-Debug):**

![Konfiguracja debugowania systemu Linux](media/linux-debug-configuration.png)

Opcje ASan są w obszarze **Ogólne**. Wprowadź flagi środowiska wykonawczego ASan w formacie "flag=value", oddzielone średnikami.

![Konfiguracja debugowania systemu Linux](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>Instalowanie symboli debugowania ASan

Aby włączyć diagnostykę ASan, należy zainstalować jego symbole debugowania (libasan-dbg) na zdalnym komputerze z systemem Linux lub instalacji WSL. Wersja libasan-dbg, którą ładujesz, zależy od wersji GCC zainstalowanej na komputerze z systemem Linux:

|**Wersja ASan**|**Wersja GCC**|
| --- | --- |
|libasan0 ( libasan0 )|gcc-4.8|
|libasan2 (libasan2)|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

Wersję GCC można określić za pomocą tego polecenia:

```bash
gcc --version
```

Aby wyświetlić wersję libasan-dbg, należy uruchomić program, a następnie spojrzeć na **debugowania** okienka **okna Dane wyjściowe.** Wersja ASan, która jest załadowana odpowiada wersji libasan-dbg potrzebne na komputerze z systemem Linux. Możesz użyć **Ctrl + F,** aby wyszukać "libasan" w oknie. Jeśli masz libasan4, na przykład, widzisz wiersz tak:

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

Bity debugowania ASan można zainstalować w dystrybucjach systemu Linux, które używają apt z następującym poleceniem. To polecenie instaluje wersję 4:

```bash
sudo apt-get install libasan4-dbg
```

Jeśli ASan jest włączona, visual studio monituje w górnej części okienka **debugowania** okna **dane wyjściowe,** aby zainstalować symbole debugowania ASan.
