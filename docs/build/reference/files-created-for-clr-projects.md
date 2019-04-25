---
title: Pliki utworzone dla projektów CLR
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
ms.openlocfilehash: 8c3e4b4187e507f7e52f8764b546f85258902879
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271046"
---
# <a name="files-created-for-clr-projects"></a>Pliki utworzone dla projektów CLR

Gdy używasz języka Visual C++, szablony do tworzenia projektów kilka plików są tworzone w zależności od szablonu możesz używać. Poniższa tabela zawiera listę wszystkich plików, które są tworzone przez Szablony projektu dla projektów programu .NET Framework.

|Nazwa pliku|Opis pliku|
|---------------|----------------------|
|AssemblyInfo.cpp|Plik zawierający informacje (oznacza to, atrybuty, pliki, zasoby, typów, informacji o wersji, informacje o podpisywaniu i tak dalej) do modyfikowania metadanych zestawu projektu. Aby uzyskać więcej informacji, zobacz [pojęcia zestawu](/dotnet/framework/app-domains/assembly-contents).|
|*projname*.asmx|Plik tekstowy, że odwołania zarządzane klas, które zapewniają funkcjonalność usługi XML sieci Web.|
|*Projname*.cpp|Główne źródło pliku i punktu wejścia do aplikacji programu Visual Studio utworzone automatycznie. Określa plik .dll projektu i przestrzeni nazw projektu. Podaj własny kod w tym pliku.|
|*projname*.vsdisco|Plik XML wdrażania, zawierające linki do innych zasobów, które opisują usługi XML sieci Web.|
|*Projname*.h|Główne dołączanego pliku projektu, który zawiera wszystkie deklaracje, symbole globalne, a `#include` dyrektywy dla innych plików nagłówkowych.|
|*projname*.sln|Plik rozwiązania, używane w środowisku deweloperskim organizować wszystkie elementy projektu w ramach jednego rozwiązania.|
|*projname*.suo|Plik opcji rozwiązanie używane w środowisku deweloperskim.|
|*Projname*.vcxproj|Plik projektu, używany w środowisku deweloperskim, która przechowuje informacje specyficzne dla tego projektu.|
|Plik ReadMe.txt|Plik opisujący każdego pliku w projekcie przy użyciu rzeczywiste nazwy plików utworzone przez szablon.|