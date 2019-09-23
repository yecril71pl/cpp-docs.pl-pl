---
title: Konfigurowanie projektów systemu Linux do używania narzędzia Address Sanitizer
description: Opisuje sposób konfigurowania C++ projektów systemu Linux w programie Visual Studio do używania adresu Sanitizer.
ms.date: 06/07/2019
ms.openlocfilehash: da7197981a431becfc1231dae96f7542062de675
ms.sourcegitcommit: b3d19b5f59f3a5d90c24f9f16c73bad4c5eb6944
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195882"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Konfigurowanie projektów systemu Linux do używania narzędzia Address Sanitizer

W programie Visual Studio 2019 w wersji 16,1, obsługa AddressSanitizer (ASan) jest zintegrowana z projektami systemu Linux. Możesz włączyć ASan dla projektów systemu Linux opartych na programie MSBuild i projektów CMake. Działa on w zdalnych systemach Linux i w podsystemie Windows dla systemu Linux (WSL).

## <a name="about-asan"></a>Informacje o ASan

ASan to detektor błędów pamięci środowiska uruchomieniowego dla językaC++ C/przechwytuje następujące błędy:

- Użyj po zwolnieniu (odwołanie do wskaźnika zawieszonego)
- Przepełnienie buforu sterty
- Przepełnienie buforu stosu
- Użyj po zwrocie
- Użyj po zakresie
- Błędy kolejności inicjowania

Gdy ASan wykryje błąd, natychmiast przestanie działać. Jeśli w debugerze zostanie uruchomiony program z obsługą ASan, zostanie wyświetlony komunikat z opisem typu błędu, adresu pamięci i lokalizacji w pliku źródłowym, w którym wystąpił błąd:

   ![ASan komunikat o błędzie](media/asan-error.png)

Możesz również wyświetlić pełne dane wyjściowe ASan (w tym miejsce, gdzie uszkodzona pamięć została przypisana/cofnięta alokacja) w okienku debugowanie w oknie danych wyjściowych.

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>Włącz ASan dla projektów systemu Linux opartych na programie MSBuild

> [!NOTE]
> Począwszy od programu Visual Studio 2019 w wersji 16,4, AddressSanitizer for Linux projekty są włączane za pośrednictwem **Właściwości** > konfiguracji**C/C++**  > Enable Address Sanitizer.

Aby włączyć ASan dla projektów systemu Linux opartych na programie MSBuild, kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie wybierz pozycję **Właściwości**. Następnie przejdź do pozycji **Właściwości** > konfiguracji**C/C++**  > **oczyszczanie**. ASan jest włączana za pośrednictwem flag kompilatora i konsolidatora i wymaga, aby projekt został ponownie skompilowany do pracy.

![Włącz ASan dla projektu MSBuild](media/msbuild-asan-prop-page.png)

Opcjonalne flagi środowiska uruchomieniowego ASan można przekazać, przechodząc do **Właściwości** > konfiguracji**debugowanie** > **flagi środowiska uruchomieniowego AddressSanitizer**. Kliknij strzałkę w dół, aby dodać lub usunąć flagi.

![Konfigurowanie flag środowiska uruchomieniowego ASan](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Włącz ASan dla projektów programu Visual Studio CMake

Aby włączyć ASan dla CMake, kliknij prawym przyciskiem myszy plik CMakeLists. txt w **Eksplorator rozwiązań** i wybierz pozycję **CMAKE ustawienia dla projektu**.

Upewnij się, że masz wybraną konfigurację systemu Linux (na przykład **Linux-Debug**) w lewym okienku okna dialogowego:

![Konfiguracja debugowania systemu Linux](media/linux-debug-configuration.png)

Opcje ASan są **Ogólne**. Wprowadź flagi środowiska uruchomieniowego ASan w formacie "Flaga = wartość" oddzielone średnikami.

![Konfiguracja debugowania systemu Linux](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>Instalowanie symboli debugowania ASan

Aby włączyć diagnostykę ASan, należy zainstalować jej symbole debugowania (libasan-DBG) na zdalnym komputerze z systemem Linux lub w instalacji WSL. Załadowana wersja libasan-DBG jest zależna od wersji programu w witrynie na komputerze z systemem Linux:

|**Wersja ASan**|**Wersja z programu w zatoce**|
| --- | --- |
|libasan0|gcc-4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

Korzystając z tego polecenia, można określić, która wersja usługi w zatoce jest dostępna:

```bash
gcc --version
```

Aby wyświetlić wymaganą wersję libasan-DBG, uruchom program, a następnie przejdź do okienka **debugowanie** w oknie **danych wyjściowych** . Załadowana wersja ASan jest zgodna z wersją libasan-DBG wymaganą na komputerze z systemem Linux. Aby wyszukać ciąg "libasan" w oknie, można użyć **kombinacji klawiszy Ctrl + F** . Jeśli masz libasan4, na przykład zobaczysz wiersz podobny do tego:

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

Usługi ASan Debug można zainstalować w systemie Linux dystrybucje, które używają apt za pomocą następującego polecenia. To polecenie służy do instalowania wersji 4:

```bash
sudo apt-get install libasan4-dbg
```

Jeśli ASan jest włączona, program Visual Studio wyświetli w górnej części okienka **debugowanie** okna **dane wyjściowe** , aby zainstalować symbole debugowania ASan.
