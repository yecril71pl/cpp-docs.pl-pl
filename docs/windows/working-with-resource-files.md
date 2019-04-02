---
title: Praca z plikami zasobów (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: 0a13fb05f0e6e8582d5e476eb889e307458f528d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767304"
---
# <a name="working-with-resource-files"></a>Praca z plikami zasobów

> [!WARNING]
> Ta sekcja dotyczy Windows aplikacji klasycznych w języku C++.
>
> Aby uzyskać informacji na temat zasobów w aplikacjach platformy uniwersalnej Windows w języku C++, zobacz [Definiowanie zasobów aplikacji](/windows/uwp/app-resources/), lub na temat dodawania zasobów dla C + +/ projektów interfejsu wiersza polecenia (zarządzane), zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w Przewodnik dewelopera .NET Framework.

Zasobów może składać się z szerokiej gamy elementów, takich jak:

- Elementy interfejsu, które zawierają informacje użytkownika, takie jak mapy bitowej, ikona lub kursor.
- Zasoby niestandardowe, które zawierają dane i aplikacja potrzebuje.
- Zasoby wersji, które są używane przez Instalatora interfejsów API.
- Menu i okien dialogowych zasoby wewnętrzne.

Można dodać nowe zasoby do projektu i zmodyfikować te zasoby za pomocą edytora odpowiedni zasób. Większość kreatorów Visual C++ automatycznie wygeneruje plik .rc w projekcie.

> [!NOTE]
> **Edytory zasobów** i **widok zasobów** nie są dostępne w wersji Express.

Aby ręcznie dodać pliki zasobów do projektów zarządzanych, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Ten artykuł zawiera instrukcje uzyskiwać dostęp do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości.

Aby sprzedawać i lokalizowania zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="in-this-section"></a>W tej sekcji

[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
Opisuje pliki zasobów i sposoby ich używania w aplikacjach pulpitu Windows. Zawiera również łącza do artykułów opisujących sposób korzystania z plików zasobów.

[Identyfikatory zasobów (symbole)](../windows/symbols-resource-identifiers.md)<br/>
Opisuje symboli i zawiera informacje na temat korzystania z **symboli zasobów** okno dialogowe, aby zarządzać symbole w swoich projektach.

[Edytory zasobów](../windows/resource-editors.md)<br/>
W tym artykule opisano edytory zasobów dostępnych w programie Visual Studio i typów zasobów, które można modyfikować za pomocą każdego edytora. Również zawiera łącza do szczegółowych informacji na temat korzystania z każdym edytorem.

## <a name="related-sections"></a>Sekcje pokrewne

[Visual C++](../overview/visual-cpp-in-visual-studio.md)<br/>
Oferuje łącza do dokumentacji języka Visual C++.

[Porozmawiaj z nami](/visualstudio/ide/talk-to-us)<br/>
Zawiera łącza do informacji na temat używania zestawu dokumentacji, kontaktując się z pomocą techniczną i wykorzystujących funkcje ułatwień dostępu.

## <a name="see-also"></a>Zobacz też

[Aplikacje pulpitu Windows](../windows/windows-desktop-applications-cpp.md)<br/>
[Menu i inne zasoby](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)