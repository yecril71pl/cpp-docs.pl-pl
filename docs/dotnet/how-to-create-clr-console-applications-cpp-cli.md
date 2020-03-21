---
title: 'Porady: tworzenie aplikacji do konsoli środowiska CLR (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
ms.openlocfilehash: 610efc8b0780422fc89e3bf9708ba488fe7d1f47
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080055"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Porady: tworzenie aplikacji do konsoli środowiska CLR (C++/CLI)

Za pomocą szablonu aplikacji konsoli można utworzyć projekt aplikacji konsoli, który ma już istotne odwołania i pliki projektu.

Zazwyczaj Aplikacja konsolowa jest kompilowana w autonomiczny plik wykonywalny, ale nie ma graficznego interfejsu użytkownika. Użytkownik uruchamia aplikację konsolową w wierszu polecenia i używa wiersza polecenia do wydawania instrukcji dla uruchomionej aplikacji. Również w wierszu polecenia aplikacja zawiera informacje wyjściowe. Immediacy aplikacji konsolowej ułatwia naukę technik programowania bez wpływu na implementację interfejsu użytkownika.

W przypadku tworzenia projektu przy użyciu szablonu Aplikacja konsolowa automatycznie dodaje te odwołania i pliki:

- Odwołania do tych przestrzeni nazw .NET Framework:

   - <xref:System.AppDomainManager>— zawiera klasy podstawowe i klasy bazowe, które definiują najczęściej używane wartości i typy danych referencyjnych, zdarzenia i procedury obsługi zdarzeń, interfejsy, atrybuty i wyjątki przetwarzania.

   - mscorlib — Biblioteka DLL zestawu, która obsługuje programowanie .NET Framework.

- Pliki źródłowe:

   - Konsola programu (plik. cpp) — główny plik źródłowy i punkt wejścia do aplikacji, która właśnie została utworzona. Identyfikuje plik Project. dll i przestrzeń nazw projektu. Podaj własny kod w tym pliku.

   - AssemblyInfo. cpp — zawiera atrybuty, pliki, zasoby, typy, informacje o wersji, informacje o podpisywaniu i tak dalej, których można użyć do modyfikowania metadanych zestawu projektu. Aby uzyskać więcej informacji, zobacz [zawartość zestawu](/dotnet/framework/app-domains/assembly-contents).

   - Stdafx. cpp — służy do kompilowania prekompilowanego pliku nagłówkowego o nazwie Win32. pch i wstępnie skompilowanego pliku o nazwie StdAfx. obj.

- Pliki nagłówkowe:

   - Stdafx. h — służy do kompilowania prekompilowanego pliku nagłówkowego o nazwie Win32. pch i wstępnie skompilowanego pliku o nazwie StdAfx. obj.

   - Resource. h — wygenerowany plik dołączania dla App. rc.

- Pliki zasobów:

   - App. RC — plik skryptu zasobu programu.

   - App. ico — plik ikony programu.

- Readme. txt — opisuje pliki w projekcie.

## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>Aby utworzyć projekt aplikacji konsoli środowiska uruchomieniowego języka wspólnego (CLR)

1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

1. W oknie dialogowym **Nowy projekt** w obszarze **zainstalowane szablony**wybierz węzeł  **C++ wizualizacji** , wybierz węzeł **CLR** , a następnie wybierz szablon aplikacja konsoli.

1. W polu **Nazwa** wprowadź unikatową nazwę aplikacji.

   Można określić inne ustawienia projektu i rozwiązania, ale nie są one wymagane.

1. Wybierz przycisk **OK** .

## <a name="see-also"></a>Zobacz też

[Projekty CLR](../build/reference/files-created-for-clr-projects.md)
