---
title: Tworzenie biblioteki DLL z samymi zasobami
description: Jak utworzyć bibliotekę DLL z samymi zasobami w programie Visual Studio.
ms.date: 01/27/2020
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
no-loc:
- noentry
ms.openlocfilehash: ef79de77e35cbef6acd4af1cec82a4edc1b7d105
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821346"
---
# <a name="creating-a-resource-only-dll"></a>Tworzenie biblioteki DLL z samymi zasobami

Biblioteka DLL tylko do zasobów jest biblioteką DLL, która nie zawiera żadnych zasobów, takich jak ikony, mapy bitowe, ciągi i okna dialogowe. Korzystanie z biblioteki DLL opartej na zasobach jest dobrym sposobem na udostępnianie tego samego zestawu zasobów między wieloma programami. Jest to również dobry sposób, aby zapewnić aplikacji zasoby zlokalizowane w wielu językach. Aby uzyskać więcej informacji, zobacz [zlokalizowane zasoby w aplikacjach MFC: satelitarne biblioteki DLL](localized-resources-in-mfc-applications-satellite-dlls.md).

## <a name="create-a-resource-only-dll"></a>Tworzenie biblioteki DLL z samymi zasobami

Aby utworzyć bibliotekę DLL tylko do zasobów, należy utworzyć nowy projekt Windows DLL (bez MFC) i dodać zasoby do projektu:

::: moniker range="vs-2015"

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **projekt Win32** . Wprowadź nazwy projektu i rozwiązania, a następnie wybierz **przycisk OK**.

1. W **Kreatorze aplikacji Win32**wybierz pozycję **Ustawienia aplikacji**. Wybierz **Typ aplikacji** **dll**. W obszarze **Opcje dodatkowe**wybierz pozycję **pusty projekt**. Wybierz pozycję **Zakończ** , aby utworzyć projekt.

1. Utwórz nowy skrypt zasobów zawierający zasoby biblioteki DLL (takie jak ciąg lub menu). Zapisz plik `.rc`.

1. W menu **projekt** wybierz opcję **Dodaj istniejący element**, a następnie Wstaw nowy plik `.rc` do projektu.

1. Określ opcję konsolidatora [/NOENTRY](reference/noentry-no-entry-point.md) . `/NOENTRY` uniemożliwia konsolidatorowi łączenie odwołania do `_main` do biblioteki DLL; Ta opcja jest wymagana do utworzenia biblioteki DLL opartej na zasobach.

1. Skompiluj bibliotekę DLL.

::: moniker-end
::: moniker range=">=vs-2017"

1. W oknie dialogowym **Nowy projekt** wybierz pozycję **Kreator pulpitu systemu Windows** , a następnie wybierz przycisk **dalej**. Na stronie **Konfiguruj nowy projekt** wprowadź nazwy projektu i rozwiązania, a następnie wybierz pozycję **Utwórz**.

1. W oknie dialogowym **projekt klasyczny systemu Windows** wybierz **Typ aplikacji** **biblioteka dołączana dynamicznie**. W obszarze **Opcje dodatkowe**wybierz pozycję **pusty projekt**. Wybierz **przycisk OK** , aby utworzyć projekt.

1. Utwórz nowy skrypt zasobów zawierający zasoby biblioteki DLL (takie jak ciąg lub menu). Zapisz plik `.rc`.

1. W menu **projekt** wybierz opcję **Dodaj istniejący element**, a następnie Wstaw nowy plik `.rc` do projektu.

1. Określ opcję konsolidatora [/NOENTRY](reference/noentry-no-entry-point.md) . `/NOENTRY` uniemożliwia konsolidatorowi łączenie odwołania do `_main` do biblioteki DLL; Ta opcja jest wymagana do utworzenia biblioteki DLL opartej na zasobach.

1. Skompiluj bibliotekę DLL.

::: moniker-end

## <a name="use-a-resource-only-dll"></a>Korzystanie z biblioteki DLL samej zasobów

Aplikacja, która korzysta z biblioteki DLL zawierającej tylko zasoby, powinna wywołać [LoadLibraryEx](loadlibrary-and-afxloadlibrary.md) lub powiązaną funkcję w celu jawnego połączenia z biblioteką DLL. Aby uzyskać dostęp do zasobów, wywołaj funkcje ogólne `FindResource` i `LoadResource`, które działają na dowolnym rodzaju zasobu. Można też wywołać jedną z następujących funkcji specyficznych dla zasobów:

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

Aplikacja powinna wywołać `FreeLibrary` po zakończeniu korzystania z zasobów.

## <a name="see-also"></a>Zobacz także

[Praca z plikami zasobów](../windows/working-with-resource-files.md)\
[Tworzenie C/C++ dll w Visual Studio](dlls-in-visual-cpp.md)
