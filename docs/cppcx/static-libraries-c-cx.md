---
title: Biblioteki statyczne (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: f62ef03cfdf2f424fd4a50c2e866d73b5bdce7fc
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302946"
---
# <a name="static-libraries-ccx"></a>Biblioteki statyczne (C++/CX)

Biblioteka statyczna, która jest używana w aplikacji platforma uniwersalna systemu Windows (platformy UWP), może zawierać kod ISO C++ Standard, w tym typy STL, a także wywołania interfejsów API Win32, które nie są wykluczone z platformy aplikacji środowisko wykonawcze systemu Windows. Biblioteka statyczna wykorzystuje składniki środowisko wykonawcze systemu Windows i może tworzyć składniki środowisko wykonawcze systemu Windows z pewnymi ograniczeniami.

## <a name="creating-static-libraries"></a>Tworzenie bibliotek statycznych


Instrukcje dotyczące tworzenia nowego projektu różnią się w zależności od zainstalowanej wersji programu Visual Studio. Upewnij się, że w lewym górnym rogu znajduje się selektor wersji w poprawnej wersji.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Aby utworzyć bibliotekę statyczną platformy UWP w programie Visual Studio 2019

1. Na pasku menu wybierz kolejno opcje **plik** > **Nowy** > **projekt** , aby otworzyć okno dialogowe **Utwórz nowy projekt** .

1. W górnej części okna dialogowego Ustaw **Język** na **C++** , ustaw **platformę** na **system Windows**i ustaw **Typ projektu** na **platformy UWP**. 

1. Z listy filtrowane typy projektów wybierz pozycję **Biblioteka statyczna (uniwersalna systemu Windows C++-/CX)** , a następnie wybierz przycisk **dalej**. Na następnej stronie Nadaj projektowi nazwę i określ lokalizację projektu w razie potrzeby.

1. Wybierz przycisk **Utwórz** , aby utworzyć projekt.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Aby utworzyć bibliotekę statyczną platformy UWP w programie Visual Studio 2017 lub Visual Studio 2015

1. Na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**. W **obszarze C++ Visual** > **system Windows Uniwersalne** Wybieranie **biblioteki statycznej (uniwersalne systemu Windows)** .

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**. W oknie dialogowym **Właściwości** na stronie **Właściwości konfiguracji** > **CC++ /** wybierz opcję Użyj **rozszerzenia środowisko wykonawcze systemu Windows** na **wartość tak (/zw)** .

::: moniker-end

Podczas kompilowania nowej biblioteki statycznej, jeśli wywołasz Win32 API, który jest wykluczony dla aplikacji platformy UWP, kompilator zgłosi błąd C3861, "nie znaleziono identyfikatora". Aby wyszukać alternatywną metodę obsługiwaną dla środowisko wykonawcze systemu Windows, zobacz [alternatywy dla interfejsów API systemu Windows w aplikacjach platformy UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

W przypadku dodania projektu C++ biblioteki statycznej do rozwiązania aplikacji platformy UWP może być konieczne zaktualizowanie ustawień właściwości projektu biblioteki, tak aby Właściwość obsługa platformy UWP została ustawiona na **wartość tak**. Bez tego ustawienia kod kompiluje i łączy, ale wystąpi błąd podczas próby zweryfikowania aplikacji dla Microsoft Store. Statyczna biblioteka lib powinna być skompilowana przy użyciu tych samych ustawień kompilatora co projekt, który go używa.

W przypadku korzystania z biblioteki statycznej, która tworzy publiczne klasy `ref`, klasy interfejsu publicznego lub publiczne klasy wartości, Konsolidator wywołuje to ostrzeżenie:

> **Ostrzeżenie LNK4264:** archiwizowanie pliku obiektu skompilowanego z/zw w bibliotece statycznej; należy pamiętać, że podczas tworzenia typów środowisko wykonawcze systemu Windows nie zaleca się łączenia z biblioteką statyczną zawierającą środowisko wykonawcze systemu Windows metadanych.

Można bezpiecznie zignorować to ostrzeżenie tylko wtedy, gdy biblioteka statyczna nie produkuje składników środowisko wykonawcze systemu Windows, które są używane poza samą biblioteką. Jeśli biblioteka nie korzysta ze zdefiniowanego przez siebie składnika, konsolidator może zoptymalizować implementację, mimo że metadane publiczne zawierają informacje o typie. Oznacza to, że składniki publiczne w bibliotece statycznej zostaną skompilowane, ale nie zostaną aktywowane w czasie wykonywania. Z tego powodu każdy składnik środowisko wykonawcze systemu Windows, który jest przeznaczony do użycia przez inne składniki lub aplikacje, musi być zaimplementowany w bibliotece dołączanej dynamicznie (DLL).

## <a name="see-also"></a>Zobacz także

[Wątkowość i marshaling](../cppcx/threading-and-marshaling-c-cx.md)
