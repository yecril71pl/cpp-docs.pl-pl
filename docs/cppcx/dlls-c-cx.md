---
title: Biblioteki DLLC++(/CX)
ms.date: 02/06/2018
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
ms.openlocfilehash: 4db0ed4f11f03c65c440c7b654653347da1d4536
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740269"
---
# <a name="dlls-ccx"></a>Biblioteki DLLC++(/CX)

Programu Visual Studio można użyć do utworzenia standardowej biblioteki DLL Win32 lub środowisko wykonawcze systemu Windows składnika DLL, który może być używany przez aplikacje platforma uniwersalna systemu Windows (platformy UWP). Standardowa biblioteka DLL, która została utworzona przy użyciu wersji programu Visual Studio lub kompilatora firmy C++ Microsoft, która jest wcześniejsza niż visual Studio 2012, może nie zostać poprawnie załadowana w aplikacji platformy UWP i nie może zostać przekazana test weryfikacji aplikacji w Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>Biblioteki DLL składników środowisko wykonawcze systemu Windows

W prawie we wszystkich przypadkach, jeśli chcesz utworzyć bibliotekę DLL do użycia w aplikacji platformy UWP, utwórz ją jako składnik środowisko wykonawcze systemu Windows przy użyciu szablonu projektu o tej nazwie. Można utworzyć projekt składnika środowisko wykonawcze systemu Windows dla bibliotek DLL, które mają typy środowisko wykonawcze systemu Windows publicznego lub prywatnego. Dostęp do składnika środowisko wykonawcze systemu Windows można uzyskać z aplikacji, które są zapisywane w dowolnym języku zgodnym z środowisko wykonawcze systemu Windows. Domyślnie ustawienia kompilatora dla projektu składnika środowisko wykonawcze systemu Windows korzystają z przełącznika **/zw** . Plik. winmd musi mieć taką samą nazwę, która ma główną przestrzeń nazw. Na przykład Klasa o nazwie A. B. C. MyClass można utworzyć wystąpienie tylko wtedy, gdy jest zdefiniowana w pliku metadanych o nazwie A. winmd lub A. B. winmd lub A. B. winmd. Nazwa biblioteki DLL nie jest wymagana, aby odpowiadała nazwie pliku winmd.

Aby uzyskać więcej informacji, zobacz [Tworzenie składników Środowisko wykonawcze systemu Windows C++w programie ](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Aby odwołać się do pliku binarnego składnika środowisko wykonawcze systemu Windows innej firmy w projekcie

1. Otwórz menu skrótów dla projektu, który będzie korzystał z biblioteki DLL, a następnie wybierz polecenie **Właściwości**. Na stronie **wspólne właściwości** wybierz przycisk **Dodaj nowe odwołanie** .

1. Składnik środowisko wykonawcze systemu Windows składa się z pliku DLL i pliku winmd, który zawiera metadane. Zazwyczaj te pliki znajdują się w tym samym folderze. W lewym okienku okna dialogowego **Dodaj odwołanie** wybierz przycisk **Przeglądaj** , a następnie przejdź do lokalizacji biblioteki DLL i pliku winmd. Aby uzyskać więcej informacji, zobacz [rozszerzenia SDK](/visualstudio/extensibility/creating-a-software-development-kit#extension-sdks).

## <a name="standard-dlls"></a>Standardowe biblioteki DLL

Można utworzyć standardową bibliotekę DLL dla C++ kodu, który nie zużywa ani nie produkuje publicznych typów środowisko wykonawcze systemu Windows i zużywa go z aplikacji platformy UWP. Użyj typu projektu biblioteka dołączana dynamicznie (DLL), jeśli chcesz tylko przeprowadzić migrację istniejącej biblioteki DLL do skompilowania w tej wersji programu Visual Studio, ale nie Konwertuj kodu na projekt składnika środowisko wykonawcze systemu Windows. W przypadku korzystania z poniższych kroków Biblioteka DLL zostanie wdrożona wraz z plikiem wykonywalnym aplikacji w pakiecie. appx.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Aby utworzyć standardową bibliotekę DLL w programie Visual Studio

1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**, a następnie wybierz szablon **biblioteka dołączana dynamicznie (dll)** .

1. Wprowadź nazwę projektu, a następnie wybierz przycisk **OK** .

1. Dodaj kod. Należy pamiętać, aby `__declspec(dllexport)` użyć dla funkcji, które mają zostać wyeksportowane — na przykład`__declspec(dllexport) Add(int I, in j);`

1. Dodaj `#include winapifamily.h` , aby dołączyć ten plik nagłówka z Windows SDK aplikacji platformy UWP i ustawić makro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Aby odwołać się do standardowego projektu DLL z tego samego rozwiązania

1. Otwórz menu skrótów dla projektu, który będzie korzystał z biblioteki DLL, a następnie wybierz polecenie **Właściwości**. Na stronie **wspólne właściwości** wybierz przycisk **Dodaj nowe odwołanie** .

1. W lewym okienku wybierz pozycję **rozwiązanie**, a następnie zaznacz odpowiednie pole wyboru w prawym okienku.

1. W plikach kodu źródłowego Dodaj `#include` instrukcję do pliku nagłówkowego dll, zgodnie z potrzebami.

### <a name="to-reference-a-standard-dll-binary"></a>Aby odwołać się do standardowej binarnej biblioteki DLL

1. Skopiuj plik DLL, plik. lib i plik nagłówkowy, a następnie wklej je w znanej lokalizacji — na przykład w bieżącym folderze projektu.

1. Otwórz menu skrótów dla projektu, który będzie korzystał z biblioteki DLL, a następnie wybierz polecenie **Właściwości**. Na stronie **Właściwości konfiguracji**, **konsolidatora**, **dane wejściowe** Dodaj plik lib jako zależność.

1. W plikach kodu źródłowego Dodaj `#include` instrukcję do pliku nagłówkowego dll, zgodnie z potrzebami.

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>Aby przeprowadzić migrację istniejącej biblioteki Win32 DLL na potrzeby zgodności aplikacji platformy UWP

1. Utwórz projekt typu DLL (uniwersalnego systemu Windows) i Dodaj do niego istniejący kod źródłowy.

1. Dodaj `#include winapifamily.h` , aby dołączyć ten plik nagłówka z Windows SDK aplikacji platformy UWP i ustawić makro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

1. W plikach kodu źródłowego Dodaj `#include` instrukcję do pliku nagłówkowego dll, zgodnie z potrzebami.
