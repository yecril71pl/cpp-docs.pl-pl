---
title: Pliki utworzone dla projektów CLR
ms.date: 11/04/2016
helpviewer_keywords:
- Visual Studio C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
ms.openlocfilehash: 45295a3395f19d32dbf29948e1cbd15cd844adb4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169009"
---
# <a name="files-created-for-clr-projects"></a>Pliki utworzone dla projektów CLR

W przypadku tworzenia projektów C++ przy użyciu szablonów wizualnych w zależności od używanego szablonu są tworzone kilka plików. W poniższej tabeli wymieniono wszystkie pliki, które są tworzone przez szablony projektu dla projektów .NET Framework.

|Nazwa pliku|Opis pliku|
|---------------|----------------------|
|AssemblyInfo. cpp|Plik zawierający informacje (czyli atrybuty, pliki, zasoby, typy, informacje o wersji, informacje o podpisywaniu itd.) w celu zmodyfikowania metadanych zestawu projektu. Aby uzyskać więcej informacji, zobacz [pojęcia związane z zestawem](/dotnet/framework/app-domains/assembly-contents).|
|*Projname*. asmx|Plik tekstowy, który odwołuje się do zarządzanych klas, które hermetyzują funkcjonalność usługi sieci Web XML.|
|*Projname*. cpp|Główny plik źródłowy i punkt wejścia do aplikacji utworzonej przez program Visual Studio. Identyfikuje plik Project. dll i przestrzeń nazw projektu. Podaj własny kod w tym pliku.|
|*Projname*. vsdisco|Plik wdrożenia XML zawierający linki do innych zasobów, które opisują usługę sieci Web XML.|
|*Projname*. h|Główny plik dołączany dla projektu, który zawiera wszystkie deklaracje, symbole globalne i dyrektywy `#include` dla innych plików nagłówkowych.|
|*Projname*. sln|Plik rozwiązania używany w środowisku deweloperskim do organizowania wszystkich elementów projektu w jednym rozwiązaniu.|
|*Projname*. suo|Plik opcji rozwiązania używany w środowisku programistycznym.|
|*Projname*. vcxproj|Plik projektu używany w środowisku deweloperskim, w którym przechowywane są informacje specyficzne dla tego projektu.|
|Plik Readme. txt|Plik opisujący każdy plik w projekcie przy użyciu rzeczywistych nazw plików utworzonych przez szablon.|
