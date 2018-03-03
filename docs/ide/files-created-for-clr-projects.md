---
title: "Pliki utworzone dla projektów CLR | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4abf5415e9b252a7cc92408fb273d226106fc16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="files-created-for-clr-projects"></a>Pliki utworzone dla projektów CLR
Użycie szablonów Visual C++ do tworzenia projektów, kilka plików są tworzone w zależności od szablonu, którego używasz. W poniższej tabeli wymieniono wszystkie pliki, które są tworzone za pomocą szablonów projektu dla projektów .NET Framework.  
  
|Nazwa pliku|Opis pliku|  
|---------------|----------------------|  
|AssemblyInfo.cpp|Plik zawierający informacje (oznacza to, atrybuty, pliki zasobów, typów, informacje na temat wersji, podpisywania informacji i itp) modyfikowania metadanych zestawu projektu. Aby uzyskać więcej informacji, zobacz [pojęcia zestawu](/dotnet/framework/app-domains/assembly-contents).|  
|*nazwa_projektu.nazwa_modułu.nazwa_procedury*.asmx|Plik tekstowy, że odwołania zarządzane klas, które zapewniają funkcje usługi XML sieci Web.|  
|*nazwa_projektu.nazwa_modułu.nazwa_procedury*.cpp|Główne źródło pliku i punktu wejścia do aplikacji tego programu Visual Studio utworzone automatycznie. Określa plik dll projektu i przestrzeń nazw projektu. Podaj kod w tym pliku.|  
|*nazwa_projektu.nazwa_modułu.nazwa_procedury*.vsdisco|Plik XML wdrożenia, zawierający łącza do innych zasobów, które opisują usługi XML sieci Web.|  
|*nazwa_projektu.nazwa_modułu.nazwa_procedury*.h|Główne dołączanego pliku projektu, który zawiera wszystkie deklaracje, symbole globalne, a `#include` dyrektywy inne pliki nagłówków.|  
|*nazwa_projektu.nazwa_modułu.nazwa_procedury*.sln|Plik rozwiązania używane w środowisku programistycznym do organizowania wszystkich elementów projektu w ramach jednego rozwiązania.|  
|*nazwa_projektu.nazwa_modułu.nazwa_procedury*.suo|Plik opcji rozwiązania używany w środowisku programistycznym.|  
|*nazwa_projektu.nazwa_modułu.nazwa_procedury*.vcxproj|Plik projektu, używany w środowisku programistycznym, która przechowuje informacje specyficzne dla tego projektu.|  
|ReadMe.txt|Plik opisujący każdego pliku w projekcie przy użyciu rzeczywiste nazwy plików utworzonych przez szablon.|