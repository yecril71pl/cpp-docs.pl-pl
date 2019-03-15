---
title: 'Instrukcje: Tworzenie weryfikowalnych projektów C++ (C + +/ CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
ms.openlocfilehash: de3742717bf55c53ab4007aaed18b6ce687fbede
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817383"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>Porady: tworzenie weryfikowalnych projektów C++ (C + +/ CLI)

Kreatory aplikacji w usłudze Visual C++ nie należy tworzyć weryfikowalnych projektów.

> [!IMPORTANT]
> Przestarzałe w programie Visual Studio 2015 i Visual Studio 2017 nie obsługuje **/CLR: pure** i **/CLR: Safe** tworzenie weryfikowalnych projektów. Jeśli potrzebujesz weryfikowalny kod, zalecamy Przetłumacz swój kod C#.

Jednak jeśli używasz starszej wersji zestawu narzędzi kompilatora Visual C++, która obsługuje **/CLR: pure** i **/CLR: Safe**, projekty mogą być konwertowane na być do sprawdzenia. W tym temacie opisano sposób ustawiania właściwości projektu i zmodyfikować pliki źródłowe projektu do przekształcania projektów Visual C++, aby tworzyć aplikacje możliwe do zweryfikowania.

## <a name="compiler-and-linker-settings"></a>Ustawienia kompilatora i konsolidatora

Domyślnie projekty .NET Użyj flagi kompilatora/CLR i skonfigurować konsolidator, aby docelowy x86 sprzętu. Weryfikowalny kod należy użyć flagi/CLR: Safe. Ponadto należy wydać konsolidator generuje MSIL zamiast instrukcji maszyny macierzystej.

### <a name="to-change-the-compiler-and-linker-settings"></a>Aby zmienić ustawienia kompilatora i konsolidatora

1. Wyświetlanie strony właściwości projektu. Aby uzyskać więcej informacji, zobacz [Ustaw kompilatora i właściwości kompilacji](../build/working-with-project-properties.md).

1. Na **ogólne** strony w obszarze **właściwości konfiguracji** zestawu węzłów, **Obsługa środowiska uruchomieniowego języka wspólnego** właściwość **bezpieczne wspólny język MSIL Obsługa środowiska uruchomieniowego (/ CLR: Safe)**.

1. Na **zaawansowane** strony w obszarze **konsolidatora** zestawu węzłów, **typu obrazu CLR** właściwości **Wymuś bezpieczny obraz IL (/ clrimagetype: Safe)**.

## <a name="removing-native-data-types"></a>Usuwanie danych natywnych typów

Ponieważ macierzyste typy danych są inne niż — możliwe do zweryfikowania, nawet jeśli nie są rzeczywiście używane, należy usunąć wszystkie pliki nagłówkowe zawierających typy natywne.

> [!NOTE]
> Poniższa procedura ma zastosowanie do projektów Windows Forms aplikacji (.NET) i Aplikacja konsoli (.NET).

### <a name="to-remove-references-to-native-data-types"></a>Aby usunąć odwołania do typów danych w trybie macierzystym

1. Komentarz w pliku Stdafx.h.

## <a name="configuring-an-entry-point"></a>Konfigurowanie punktu wejścia

Ponieważ weryfikowalny aplikacje nie mogą używać biblioteki wykonawczej C (CRT), nie są one zależne od CRT, aby wywołać funkcję main jako punkt wejścia standardowego. Oznacza to, należy jawnie określić nazwę funkcji do wywołania początkowo do konsolidatora. (W tym przypadku Main() jest używany zamiast main() lub _tmain() do wskazania punktem wejścia bez CRT, ale ponieważ punktu wejścia muszą być jawnie określone, ta nazwa jest dowolnego.)

> [!NOTE]
> Poniższe procedury dotyczą projekty aplikacji konsoli (.NET).

#### <a name="to-configure-an-entry-point"></a>Aby skonfigurować punkt wejścia

1. Zmień _tmain() Main() w pliku .cpp głównego projektu.

1. Wyświetlanie strony właściwości projektu. Aby uzyskać więcej informacji, zobacz [Ustaw kompilatora i właściwości kompilacji](../build/working-with-project-properties.md).

1. Na **zaawansowane** strony w obszarze **konsolidatora** węzła, wprowadź `Main` jako **punktu wejścia** wartości właściwości.

## <a name="see-also"></a>Zobacz także

- [Kod czysty i weryfikowalny (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
