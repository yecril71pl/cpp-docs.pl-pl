---
title: Biblioteki dll (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/06/2018
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16b7ed16ec128f1fbf67d1b62e974ccd7ea5213b
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="dlls-ccx"></a>Biblioteki dll (C + +/ CX)

Visual Studio umożliwia utworzenie standardowego DLL Win32 lub składnik środowiska wykonawczego systemu Windows biblioteki DLL, które mogą być używane przez aplikacje systemu Windows platformy Uniwersalnej. Standardowe biblioteki DLL, który został utworzony przy użyciu wersji programu Visual Studio lub kompilator języka Visual C++, która jest starsza niż programu Visual Studio 2012 nie można prawidłowo załadować w aplikacji platformy uniwersalnej systemu Windows i nie mogą przechodzić test weryfikacji aplikacji w Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>Biblioteki DLL składnika środowiska wykonawczego systemu Windows

W większości przypadków gdy chcesz utworzyć biblioteki DLL dla używanie w aplikacji platformy uniwersalnej systemu Windows, utwórz go jako składnik środowiska wykonawczego systemu Windows za pomocą szablonu projektu o tej nazwie. Projekt składnika środowiska wykonawczego systemu Windows można utworzyć dla bibliotek DLL, które mają publicznych lub prywatnych typów środowiska wykonawczego systemu Windows. Składnik środowiska wykonawczego systemu Windows są dostępne z aplikacji, które są zapisywane w dowolnym języku zgodnym środowiska wykonawczego systemu Windows. Domyślnie ustawienia kompilatora dla składnika środowiska wykonawczego systemu Windows projektu użyj **/ZW** przełącznika. Plik winmd musi mieć takiej samej nazwie, który ma głównej przestrzeni nazw. Na przykład klasy o nazwie A.B.C.MyClass można wdrożyć tylko wtedy, gdy jest on zdefiniowany w pliku metadanych o nazwie A.winmd lub A.B.winmd lub A.B.C.winmd. Nazwę biblioteki DLL nie musi być zgodna z nazwą pliku winmd.

Aby uzyskać więcej informacji, zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Aby odwołać binarne w projekcie składnika środowiska wykonawczego systemu Windows innych firm

1. Otwórz menu skrótów projektu, który będzie używać biblioteki DLL, a następnie wybierz pozycję **właściwości**. Na **wspólne właściwości** wybierz pozycję **Dodaj nowe odwołanie** przycisku.

1. Składnik środowiska wykonawczego systemu Windows składa się z pliku DLL i plik winmd, który zawiera metadanych. Zazwyczaj te pliki znajdują się w tym samym folderze. W lewym okienku **Dodaj odwołanie** oknie dialogowym wybierz **Przeglądaj** przycisk, a następnie przejdź do lokalizacji pliku DLL i jego pliku winmd. Aby uzyskać więcej informacji, zobacz [rozszerzenia SDK](/visualstudio/extensibility/creating-a-software-development-kit#ExtensionSDKs).

## <a name="standard-dlls"></a>Standardowych bibliotek DLL

Możesz utworzyć standardowe biblioteki DLL dla kodu C++, który nie używać lub utworzyć typy publiczne środowiska wykonawczego systemu Windows i pobrać go z aplikacji platformy uniwersalnej systemu Windows. Należy używać typu projektu biblioteki dołączanej dynamicznie (DLL), gdy chcesz migrować istniejące biblioteki DLL do kompilacji w tej wersji programu Visual Studio, ale nie Konwertuj kod na projekt składnika środowiska wykonawczego systemu Windows. Podczas korzystania z następujących kroków, plik DLL, który zostanie wdrożony obok pliku wykonywalnego w pakiecie appx aplikacji.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Aby utworzyć standardowe biblioteki DLL w programie Visual Studio

1. Na pasku menu wybierz **pliku**, **nowy**, **projektu**, a następnie wybierz **dynamiczne łącze Biblioteka (DLL)** szablonu.

1. Wprowadź nazwę dla projektu, a następnie wybierz pozycję **OK** przycisku.

1. Dodaj kod. Należy użyć `__declspec(dllexport)` dla funkcji, które chcesz wyeksportować — na przykład `__declspec(dllexport) Add(int I, in j);`

1. Dodaj `#include winapifamily.h` dołączyć ten plik nagłówka z zestawu Windows SDK dla aplikacji platformy uniwersalnej systemu Windows i ustaw `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Aby odwołać standardowe projektu biblioteki DLL z tym samym rozwiązaniu

1. Otwórz menu skrótów projektu, który będzie używać biblioteki DLL, a następnie wybierz pozycję **właściwości**. Na **wspólne właściwości** wybierz pozycję **Dodaj nowe odwołanie** przycisku.

1. W okienku po lewej stronie wybierz **rozwiązania**, a następnie wybierz odpowiednie pole wyboru w okienku po prawej stronie.

1. W plikach kodu źródłowego, Dodaj `#include` instrukcji dla nagłówka pliku DLL, zgodnie z potrzebami.

### <a name="to-reference-a-standard-dll-binary"></a>Aby odwołać standardowego pliku binarnego biblioteki DLL

1. Skopiuj plik DLL, plików lib i plik nagłówka i wklej je w znanej lokalizacji — na przykład w bieżącym folderze projektu.

1. Otwórz menu skrótów projektu, który będzie używać biblioteki DLL, a następnie wybierz pozycję **właściwości**. Na **właściwości konfiguracji**, **konsolidatora**, **dane wejściowe** strony, należy dodać do pliku .lib jako zależności.

1. W plikach kodu źródłowego, Dodaj `#include` instrukcji dla nagłówka pliku DLL, zgodnie z potrzebami.

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>Aby przeprowadzić migrację istniejącej biblioteki DLL Win32 dla zgodności aplikacji platformy uniwersalnej systemu Windows

1. Tworzenie projektu typu DLL (uniwersalna systemu Windows) i Dodaj do niej istniejącego kodu źródłowego.

1. Dodaj `#include winapifamily.h` dołączyć ten plik nagłówka z zestawu Windows SDK dla aplikacji platformy uniwersalnej systemu Windows i ustaw `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

1. W plikach kodu źródłowego, Dodaj `#include` instrukcji dla nagłówka pliku DLL, zgodnie z potrzebami.
