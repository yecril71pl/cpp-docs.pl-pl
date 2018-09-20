---
title: Pliki utworzone dla projektów CLR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bd76a978c1c85969883b8222097f29f501fd960
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385355"
---
# <a name="files-created-for-clr-projects"></a>Pliki utworzone dla projektów CLR

Gdy używasz języka Visual C++, szablony do tworzenia projektów kilka plików są tworzone w zależności od szablonu możesz używać. Poniższa tabela zawiera listę wszystkich plików, które są tworzone przez Szablony projektu dla projektów programu .NET Framework.

|Nazwa pliku|Opis pliku|
|---------------|----------------------|
|AssemblyInfo.cpp|Plik zawierający informacje (oznacza to, atrybuty, pliki, zasoby, typów, informacji o wersji, informacje o podpisywaniu i tak dalej) do modyfikowania metadanych zestawu projektu. Aby uzyskać więcej informacji, zobacz [pojęcia zestawu](/dotnet/framework/app-domains/assembly-contents).|
|*projname*asmx|Plik tekstowy, że odwołania zarządzane klas, które zapewniają funkcjonalność usługi XML sieci Web.|
|*Projname*.cpp|Główne źródło pliku i punktu wejścia do aplikacji programu Visual Studio utworzone automatycznie. Określa plik .dll projektu i przestrzeni nazw projektu. Podaj własny kod w tym pliku.|
|*projname*.vsdisco|Plik XML wdrażania, zawierające linki do innych zasobów, które opisują usługi XML sieci Web.|
|*Projname*.h|Główne dołączanego pliku projektu, który zawiera wszystkie deklaracje, symbole globalne, a `#include` dyrektywy dla innych plików nagłówkowych.|
|*projname*SLN|Plik rozwiązania, używane w środowisku deweloperskim organizować wszystkie elementy projektu w ramach jednego rozwiązania.|
|*Projname*.suo|Plik opcji rozwiązanie używane w środowisku deweloperskim.|
|*Projname*.vcxproj|Plik projektu, używany w środowisku deweloperskim, która przechowuje informacje specyficzne dla tego projektu.|
|Plik ReadMe.txt|Plik opisujący każdego pliku w projekcie przy użyciu rzeczywiste nazwy plików utworzone przez szablon.|