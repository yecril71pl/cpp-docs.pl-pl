---
title: DLLs (C++/CX)
ms.date: 02/06/2018
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
ms.openlocfilehash: 1a72ecc5eb46abfbc7b9a52a168510ce0873ee04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183291"
---
# <a name="dlls-ccx"></a>DLLs (C++/CX)

Visual Studio umożliwia tworzenie standardowego DLL Win32 lub składnik środowiska uruchomieniowego Windows DLL, które mogą być używane przez aplikacje platformy uniwersalnej Windows (UWP). Standardowe biblioteki DLL, który został utworzony przy użyciu wersji programu Visual Studio lub przez kompilator Visual C++, który jest wcześniejsza niż Visual Studio 2012 nie można prawidłowo załadować w aplikacji platformy uniwersalnej systemu Windows i nie może przekazać test weryfikacyjny z aplikacji Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>Biblioteki DLL składnika środowiska wykonawczego Windows

Prawie we wszystkich przypadkach gdy chcesz utworzyć biblioteki DLL dla używanie w aplikacji platformy uniwersalnej systemu Windows, utwórz go jako składnik środowiska wykonawczego Windows, za pomocą szablonu projektu o takiej nazwie. Można utworzyć projekt składnika środowiska wykonawczego Windows, dla bibliotek DLL, które mają publiczne lub prywatne typów środowiska wykonawczego Windows. Składnik środowiska uruchomieniowego Windows są dostępne z aplikacji, które zostały napisane w dowolnym języku zgodnym z Windows Runtime. Domyślnie ustawienia kompilatora składnika środowiska uruchomieniowego Windows projektu użyj **/ZW** przełącznika. Pliku winmd musi mieć taką samą nazwę, który ma głównej przestrzeni nazw. Na przykład klasa, która nosi nazwę A.B.C.MyClass wystąpienia można tworzyć tylko wtedy, gdy jest on zdefiniowany w pliku metadanych, który nosi nazwę A.winmd i A.B.winmd lub A.B.C.winmd. Nazwa pliku DLL, nie musi być zgodna z nazwą pliku .winmd.

Aby uzyskać więcej informacji, zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Można się odwoływać do składnika Windows Runtime firm binarnym w projekcie

1. Otwórz menu skrótów dla projektu, który będzie używać biblioteki DLL, a następnie wybierz **właściwości**. Na **wspólne właściwości** wybierz **Dodaj nowe odwołanie** przycisku.

1. Składnik środowiska uruchomieniowego Windows składa się z pliku DLL i plik .winmd, który zawiera metadane. Zazwyczaj te pliki znajdują się w tym samym folderze. W okienku po lewej stronie **Dodaj odwołanie** okna dialogowego wybierz **Przeglądaj** przycisk, a następnie przejdź do lokalizacji pliku DLL i jego pliku winmd. Aby uzyskać więcej informacji, zobacz [zestawów SDK rozszerzeń](/visualstudio/extensibility/creating-a-software-development-kit#ExtensionSDKs).

## <a name="standard-dlls"></a>Standardowe biblioteki dll

Można utworzyć standardowe biblioteki DLL dla kodu C++, który nie zużywają lub utworzyć publiczny typów środowiska wykonawczego Windows i stosować go z aplikacji platformy uniwersalnej systemu Windows. Gdy chcesz przeprowadzić migrację istniejącej biblioteki DLL do kompilacji w tej wersji programu Visual Studio, ale nie skonwertować kod projekt składnika środowiska wykonawczego Windows, należy użyć typu projektu Biblioteka dołączana dynamicznie (DLL). Korzystając z następujących czynności, zostanie wdrożony biblioteki DLL wraz z aplikacją wykonywalnego w pakiecie .appx.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Aby utworzyć standardowe biblioteki DLL w programie Visual Studio

1. Na pasku menu wybierz **pliku**, **New**, **projektu**, a następnie wybierz pozycję **dynamiczne łączy biblioteki (DLL)** szablonu.

1. Wprowadź nazwę dla projektu, a następnie wybierz **OK** przycisku.

1. Dodaj kod. Należy użyć `__declspec(dllexport)` dla funkcji, które chcesz wyeksportować — na przykład `__declspec(dllexport) Add(int I, in j);`

1. Dodaj `#include winapifamily.h` do uwzględnienia pliku nagłówka z zestawu Windows SDK dla platformy uwp, a następnie ustaw makro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Aby odwoływać się do standardowych projektu biblioteki DLL z tym samym rozwiązaniu

1. Otwórz menu skrótów dla projektu, który będzie używać biblioteki DLL, a następnie wybierz **właściwości**. Na **wspólne właściwości** wybierz **Dodaj nowe odwołanie** przycisku.

1. W okienku po lewej stronie wybierz **rozwiązania**, a następnie zaznacz odpowiednie pole wyboru w okienku po prawej stronie.

1. W plikach kodu źródłowego, Dodaj `#include` instrukcja dla nagłówka pliku DLL, zgodnie z potrzebami.

### <a name="to-reference-a-standard-dll-binary"></a>Aby odwoływać się do standardowych binary biblioteki DLL

1. Skopiuj plik DLL, plik .lib i pliku nagłówka, a następnie wklej je w znanej lokalizacji — na przykład w bieżącym folderze projektu.

1. Otwórz menu skrótów dla projektu, który będzie używać biblioteki DLL, a następnie wybierz **właściwości**. Na **właściwości konfiguracji**, **konsolidatora**, **dane wejściowe** strony, należy dodać plik .lib jako zależność.

1. W plikach kodu źródłowego, Dodaj `#include` instrukcja dla nagłówka pliku DLL, zgodnie z potrzebami.

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>Aby przeprowadzić migrację istniejących bibliotek DLL systemu Win32 dla zgodności aplikacji platformy uniwersalnej systemu Windows

1. Tworzenie projektu typu DLL (Windows Universal) i Dodaj istniejący kod źródłowy do niego.

1. Dodaj `#include winapifamily.h` do uwzględnienia pliku nagłówka z zestawu Windows SDK dla platformy uwp, a następnie ustaw makro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

1. W plikach kodu źródłowego, Dodaj `#include` instrukcja dla nagłówka pliku DLL, zgodnie z potrzebami.
