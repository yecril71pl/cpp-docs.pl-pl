---
title: Biblioteki statyczne (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 3c4bfd28b805903a2e596ef6d648ff31b0b8261c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358110"
---
# <a name="static-libraries-ccx"></a>Biblioteki statyczne (C++/CX)

Biblioteka statyczna używana w aplikacji platformy uniwersalnej systemu Windows (UWP) może zawierać standardowy kod C++, w tym typy STL, a także wywołania interfejsów API systemu Win32, które nie są wykluczone z platformy aplikacji środowiska wykonawczego systemu Windows. Biblioteka statyczna zużywa składniki środowiska wykonawczego systemu Windows i może tworzyć składniki środowiska wykonawczego systemu Windows z pewnymi ograniczeniami.

## <a name="creating-static-libraries"></a>Tworzenie bibliotek statycznych

Instrukcje dotyczące tworzenia nowego projektu różnią się w zależności od wersji programu Visual Studio, które zostały zainstalowane. Aby wyświetlić dokumentację preferowanej wersji programu Visual Studio, użyj formantu selektor **wersji.** Znajduje się w górnej części spisu treści na tej stronie.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Aby utworzyć bibliotekę statyczną platformy uniwersalnej systemu zutylizanego w programie Visual Studio 2019

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu,** aby otworzyć okno dialogowe Tworzenie nowego **projektu.**

1. W górnej części okna dialogowego ustaw **język** na **C++**, ustaw **platformę** na **Windows**i ustaw **typ projektu** na **platformy uniwersalnej systemu Windows**.

1. Z filtru listy typów projektów wybierz pozycję **Biblioteka statyczna (Universal Windows - C++/CX),** a następnie wybierz pozycję **Dalej**. Na następnej stronie nadaj projektowi nazwę i w razie potrzeby określ lokalizację projektu.

1. Wybierz przycisk **Utwórz,** aby utworzyć projekt.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Aby utworzyć bibliotekę statyczną platformy uniwersalnej systemu Wizjudy w programie Visual Studio 2017 lub visual studio 2015

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W **obszarze Visual C++** > **Windows Universal** wybierz **bibliotekę statyczną (universal Windows)**.

1. W **Eksploratorze rozwiązań**otwórz menu **skrótów**dla projektu, a następnie wybierz polecenie Właściwości . W oknie dialogowym **Właściwości** na stronie **Właściwości** > konfiguracji**C/C++** ustaw **opcję Zużywają rozszerzenie środowiska wykonawczego systemu Windows** na Tak **(ZW).**

::: moniker-end

Podczas kompilowania nowej biblioteki statycznej, jeśli wywołasz interfejs API Usługi Win32, który jest wykluczony dla aplikacji platformy uniwersalnej systemu Windows, kompilator będzie podnosić błąd C3861, "Identyfikator nie znaleziono." Aby wyszukać alternatywną metodę obsługiwaną dla środowiska wykonawczego systemu Windows, zobacz [Alternatywy dla interfejsów API systemu Windows w aplikacjach platformy uniwersalnej systemu Windows](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Jeśli dodasz projekt biblioteki statycznej języka C++ do rozwiązania aplikacji platformy uniwersalnej systemu Windows, może być trzeba zaktualizować ustawienia właściwości projektu biblioteki, tak aby właściwość pomocy technicznej platformy uniwersalnej systemu Windows była ustawiona na **Tak**. Bez tego ustawienia kod tworzy i łączy, ale błąd występuje podczas próby zweryfikowania aplikacji dla Microsoft Store. Lib statyczne powinny być kompilowane z tymi samymi ustawieniami kompilatora jako projekt, który zużywa go.

Jeśli używasz biblioteki statycznej, która tworzy klasy publiczne, `ref` klasy interfejsu publicznego lub klasy wartości publicznej, konsolidator wywołuje to ostrzeżenie:

> **ostrzeżenie LNK4264:** archiwizacja pliku obiektu skompilowanego z /ZW do biblioteki statycznej; Należy zauważyć, że podczas tworzenia typów środowiska wykonawczego systemu Windows nie zaleca się łączenia z biblioteką statyczną zawierającą metadane środowiska wykonawczego systemu Windows.

Ostrzeżenie można bezpiecznie zignorować tylko wtedy, gdy biblioteka statyczna nie tworzy składników środowiska wykonawczego systemu Windows, które są używane poza samą biblioteką. Jeśli biblioteka nie zużywa składnik, który definiuje, a następnie konsolidator można zoptymalizować od implementacji, nawet jeśli publiczne metadane zawiera informacje o typie. Oznacza to, że składniki publiczne w bibliotece statycznej będą kompilowane, ale nie zostaną aktywowane w czasie wykonywania. Z tego powodu każdy składnik środowiska wykonawczego systemu Windows, który jest przeznaczony do użycia przez inne składniki lub aplikacje, musi zostać zaimplementowany w bibliotece łącza dynamicznego (DLL).

## <a name="see-also"></a>Zobacz też

[Wątkowość i marshaling](../cppcx/threading-and-marshaling-c-cx.md)
