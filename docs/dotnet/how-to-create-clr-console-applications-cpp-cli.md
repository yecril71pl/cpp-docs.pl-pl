---
title: 'Porady: tworzenie aplikacji do konsoli środowiska CLR (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
ms.openlocfilehash: 86e5abe330b0edc514fed74a12188ab73e8bfdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368533"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Porady: tworzenie aplikacji do konsoli środowiska CLR (C++/CLI)

Za pomocą szablonu aplikacji konsoli można utworzyć projekt aplikacji konsoli, który ma już istotne odwołania do projektu i pliki.

Zazwyczaj aplikacja konsoli jest kompilowana do autonomicznego pliku wykonywalnego, ale nie ma graficznego interfejsu użytkownika. Użytkownik uruchamia aplikację konsoli w wierszu polecenia i używa wiersza polecenia do wydawania instrukcji do uruchomionej aplikacji. Również w wierszu polecenia aplikacja udostępnia informacje wyjściowe. Bezpośredniość aplikacji konsoli sprawia, że jest to świetny sposób, aby nauczyć się technik programowania bez obawy o implementację interfejsu użytkownika.

Podczas tworzenia projektu za pomocą szablonu aplikacji konsoli automatycznie dodaje te odwołania i pliki:

- Odwołania do tych obszarów nazw programu .NET Framework:

  - <xref:System.AppDomainManager>— zawiera podstawowe klasy i klasy podstawowe, które definiują powszechnie używane wartości i typy danych referencyjnych, zdarzenia i programy obsługi zdarzeń, interfejsy, atrybuty i wyjątki przetwarzania.

  - mscorlib — biblioteka DLL zestawu obsługująca program .NET Framework.

- Pliki źródłowe:

  - Konsola (plik cpp)— główny plik źródłowy i punkt wejścia do właśnie utworzonej aplikacji. Identyfikuje plik dll projektu i obszar nazw projektu. Podaj własny kod w tym pliku.

  - AssemblyInfo.cpp — zawiera atrybuty, pliki, zasoby, typy, informacje o wersji, informacje o podpisywaniu i tak dalej, że można użyć do modyfikowania metadanych zestawu projektu. Aby uzyskać więcej informacji, zobacz [Zawartość zestawu](/dotnet/framework/app-domains/assembly-contents).

  - Stdafx.cpp — służy do tworzenia wstępnie skompilowanego pliku nagłówka o nazwie Win32.pch i wstępnie skompilowanego pliku typów o nazwie StdAfx.obj.

- Pliki nagłówkowe:

  - Stdafx.h — służy do tworzenia wstępnie skompilowanego pliku nagłówka o nazwie Win32.pch i wstępnie skompilowanego pliku typów o nazwie StdAfx.obj.

  - resource.h — wygenerowany plik dołączania dla pliku app.rc.

- Pliki zasobów:

  - app.rc — plik skryptu zasobów programu.

  - app.ico — plik ikon programu.

- ReadMe.txt — opisuje pliki w projekcie.

## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>Aby utworzyć projekt aplikacji konsoli wspólnego środowiska wykonawczego języka (CLR)

1. Na pasku menu wybierz pozycję **Plik**, **Nowy**, **Projekt**.

1. W oknie dialogowym **Nowy projekt** w obszarze **Zainstalowane szablony**wybierz węzeł **Visual C++,** wybierz węzeł **CLR,** a następnie wybierz szablon aplikacji konsoli.

1. W polu **Nazwa** wprowadź unikatową nazwę aplikacji.

   Można określić inne ustawienia projektu i rozwiązania, ale nie są one wymagane.

1. Wybierz przycisk **OK.**

## <a name="see-also"></a>Zobacz też

[Projekty CLR](../build/reference/files-created-for-clr-projects.md)
