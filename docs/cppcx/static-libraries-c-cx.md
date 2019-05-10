---
title: Biblioteki statyczne (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 188ba06518bf6cdd154b7d6bd61216ed1e4ffad3
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877243"
---
# <a name="static-libraries-ccx"></a>Biblioteki statyczne (C++/CX)

Bibliotekę statyczną, który jest używany w aplikacji platformy uniwersalnej Windows (UWP) może zawierać kod ISO standard C++, takich jak typy STL i wywołań interfejsów API systemu Win32, które nie są wykluczone z platformy aplikacji środowiska wykonawczego Windows. Biblioteka statyczna wykorzystuje składników środowiska wykonawczego Windows i mogą tworzyć składniki środowiska wykonawczego Windows pewne ograniczenia.

## <a name="creating-static-libraries"></a>Tworzenie bibliotek statycznych


Instrukcje dotyczące tworzenia nowego projektu zależy od zainstalowanej wersji programu Visual Studio. Upewnij się, że w selektorze wersja w prawym górnym lewym równa poprawnej wersji.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Do tworzenia biblioteki statycznej platformy uniwersalnej systemu Windows w programie Visual Studio 2019 r.

1. Na pasku menu wybierz **pliku** > **New** > **projektu** otworzyć **Utwórz nowy projekt** okno dialogowe.

1. W górnej części okna dialogowego, ustaw **języka** do **C++** ustaw **platformy** do **Windows**i ustaw **Typprojektu** do **platformy uniwersalnej systemu Windows**. 

1. Wybierz z listy filtrowanej typów projektów, **biblioteka statyczna (Windows Universal - C++/CX)** wybierz **dalej**. Na następnej stronie nazwij projekt, a następnie określ lokalizację projektu, w razie potrzeby.

1. Wybierz **Utwórz** przycisk, aby utworzyć projekt.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Do tworzenia biblioteki statycznej platformy uniwersalnej systemu Windows w programie Visual Studio 2017 lub Visual Studio 2015

1. Na pasku menu wybierz **pliku** > **New** > **projektu**. W obszarze **Visual C++** > **Windows Universal** wybierz **biblioteka statyczna (Windows Universal)**.

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**. W **właściwości** dialogowym **właściwości konfiguracji** > **C/C++** ustaw **używanie rozszerzenia środowiska uruchomieniowego Windows** do **tak (/ZW)**.

::: moniker-end

Podczas kompilowania nowe biblioteki statycznej, jeśli wywołanie interfejsu API Win32, który jest wyłączone dla aplikacji platformy UWP, czasami kompilator zgłosi błąd C3861, "Nie odnaleziono identyfikatora." Aby wyszukać alternatywną metodę, która jest obsługiwana dla środowiska wykonawczego Windows, zobacz [alternatywy dla Windows API w aplikacjach platformy UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Jeśli dodasz projekt statycznej biblioteki języka C++ do rozwiązania aplikacji platformy uniwersalnej systemu Windows, Niewykluczone, że można zaktualizować ustawień właściwości projektu biblioteki, tak aby właściwość pomocy technicznej platformy uniwersalnej systemu Windows jest ustawiona na **tak**. Bez tego ustawienia kod zostanie skompilowany i linki, ale błąd występuje, gdy użytkownik podejmie sprawdzić, czy aplikacja Microsoft Store. Statycznej lib powinna być skompilowana przy użyciu tych samych ustawień kompilatora jako projekt, który ich używa.

Jeśli wykorzystasz bibliotekę statyczną, która tworzy publiczny `ref` klasy, klasy publicznego interfejsu lub klasy publicznej wartości, konsolidator generuje to ostrzeżenie:

> **Ostrzeżenie LNK4264:** archiwizowanie pliku obiektu skompilowanego z parametrem /ZW do biblioteki statycznej; należy pamiętać, że podczas tworzenia typów środowiska wykonawczego Windows nie zaleca się połączyć z biblioteką statyczną zawierającą metadane środowiska wykonawczego Windows.

Można bezpiecznie zignorować to ostrzeżenie, tylko wtedy, gdy biblioteka statyczna nie daje składników środowiska wykonawczego Windows, które są używane poza sama biblioteka. Jeśli biblioteka nie wykorzystasz składnik, który definiuje, następnie konsolidator może optymalizują wdrożenia, nawet jeśli publiczny metadane zawierają informacje o typie. Oznacza to, że publiczne składniki w bibliotece statycznej zostanie skompilowany, ale nie zostanie aktywowany w czasie wykonywania. Z tego powodu dowolny Windows Runtime składnik, który jest przeznaczony do użytku przez inne składniki lub aplikacje muszą zostać zaimplementowane w biblioteki dołączanej (dynamicznie DLL).

## <a name="see-also"></a>Zobacz także

[Wątkowość i marshaling](../cppcx/threading-and-marshaling-c-cx.md)
