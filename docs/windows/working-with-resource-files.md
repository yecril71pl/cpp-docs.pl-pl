---
title: Praca z plikami zasobów (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: 142a9120e0b6b95e659fcb47c275653fbefd8cbe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165889"
---
# <a name="working-with-resource-files"></a>Praca z plikami zasobów

> [!WARNING]
> Ta sekcja dotyczy aplikacji klasycznych systemu Windows utworzonych C++w systemie.
>
> Aby uzyskać informacje o zasobach w platforma uniwersalna systemu Windows aplikacjach C++pisanych w systemie, zobacz [Definiowanie zasobów aplikacji](/windows/uwp/app-resources/)lub Dodawanie zasobów C++do projektów/CLI (zarządzanych), zobacz artykuł [zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index) w przewodniku .NET Framework dewelopera.

Zasoby mogą składać się z szerokiego zakresu elementów, takich jak:

- Elementy interfejsu, które dostarczają informacje dla użytkownika, takie jak mapa bitowa, ikona lub kursor.
- Zasoby niestandardowe, które zawierają wymagania dotyczące danych i aplikacji.
- Zasoby wersji, które są używane przez Instalatora interfejsów API.
- Zasoby menu i okna dialogowego.

Do projektu można dodawać nowe zasoby i modyfikować je za pomocą odpowiedniego edytora zasobów. Większość kreatorów wizualizacji C++ automatycznie generuje plik. RC dla projektu.

> [!NOTE]
> **Edytory zasobów** i **Widok zasobów** nie są dostępne w wersjach Express.

Aby ręcznie dodać pliki zasobów do projektów zarządzanych, zobacz [Tworzenie plików zasobów dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). W tym artykule opisano sposób uzyskiwania dostępu do zasobów, wyświetlania zasobów statycznych i przypisywania ciągów zasobów do właściwości.

Aby przeprowadzić globalizację i lokalizowanie zasobów w zarządzanych aplikacjach, zobacz [globalizacja i lokalizowanie aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="in-this-section"></a>W tej sekcji

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
Opisuje pliki zasobów i sposób ich używania w aplikacjach klasycznych systemu Windows. Zawiera również linki do artykułów opisujących sposób używania plików zasobów.

[Identyfikatory zasobów (symbole)](../windows/symbols-resource-identifiers.md)<br/>
Zawiera opis symboli i zawiera informacje na temat używania okna dialogowego **symbole zasobów** do zarządzania symbolami w projektach.

[Edytory zasobów](../windows/resource-editors.md)<br/>
Opisuje edytory zasobów dostępne w programie Visual Studio oraz typy zasobów, które można modyfikować za pomocą każdego edytora. Oferuje także linki do szczegółowych informacji na temat korzystania z poszczególnych edytorów.

## <a name="related-sections"></a>Sekcje pokrewne

[Język C++ w programie Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
Oferuje łącza do dokumentacji języka Visual C++.

[Porozmawiaj z nami](/visualstudio/ide/talk-to-us)<br/>
Zawiera łącza do informacji na temat korzystania z zestawu dokumentacji, kontaktowania się z pomocą techniczną i używania funkcji ułatwień dostępu.

## <a name="see-also"></a>Zobacz też

[Aplikacje klasyczne systemu Windows](../windows/windows-desktop-applications-cpp.md)<br/>
[Menu i inne zasoby](/windows/win32/menurc/resources)
