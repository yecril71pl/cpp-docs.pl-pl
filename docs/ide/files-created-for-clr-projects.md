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
ms.openlocfilehash: b9d66c3f55164a743bc395dc5e9b48f8bcd57654
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33334668"
---
# <a name="files-created-for-clr-projects"></a>Pliki utworzone dla projektów CLR
Użycie szablonów Visual C++ do tworzenia projektów, kilka plików są tworzone w zależności od szablonu, którego używasz. W poniższej tabeli wymieniono wszystkie pliki, które są tworzone za pomocą szablonów projektu dla projektów .NET Framework.  
  
|Nazwa pliku|Opis pliku|  
|---------------|----------------------|  
|AssemblyInfo.cpp|Plik zawierający informacje (oznacza to, atrybuty, pliki zasobów, typów, informacje na temat wersji, podpisywania informacji i itp) modyfikowania metadanych zestawu projektu. Aby uzyskać więcej informacji, zobacz [pojęcia zestawu](/dotnet/framework/app-domains/assembly-contents).|  
|*nazwa_projektu.nazwa_modułu.nazwa_procedury*.asmx|Plik tekstowy, że odwołania zarządzane klas, które zapewniają funkcje usługi XML sieci Web.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.cpp|Główne źródło pliku i punktu wejścia do aplikacji tego programu Visual Studio utworzone automatycznie. Określa plik dll projektu i przestrzeń nazw projektu. Podaj kod w tym pliku.|  
|*nazwa_projektu.nazwa_modułu.nazwa_procedury*.vsdisco|Plik XML wdrożenia, zawierający łącza do innych zasobów, które opisują usługi XML sieci Web.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.h|Główne dołączanego pliku projektu, który zawiera wszystkie deklaracje, symbole globalne, a `#include` dyrektywy inne pliki nagłówków.|  
|*nazwa_projektu.nazwa_modułu.nazwa_procedury*.sln|Plik rozwiązania używane w środowisku programistycznym do organizowania wszystkich elementów projektu w ramach jednego rozwiązania.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.suo|Plik opcji rozwiązania używany w środowisku programistycznym.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.vcxproj|Plik projektu, używany w środowisku programistycznym, która przechowuje informacje specyficzne dla tego projektu.|  
|ReadMe.txt|Plik opisujący każdego pliku w projekcie przy użyciu rzeczywiste nazwy plików utworzonych przez szablon.|