---
title: Informacje o tworzeniu manifestu dla programów C/C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40dbc61009cdfaa5621335cfb78dd10eae2138ca
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465048"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Ogólne informacje o tworzeniu manifestu dla programów C/C++
A [manifestu](http://msdn.microsoft.com/library/aa375365) jest dokument XML, który może być plik XML lub zasób osadzony w aplikacji lub zestawu. Manifest [izolowany aplikacji](http://msdn.microsoft.com/library/aa375190) służy do zarządzania nazwami i wersjami współużytkowanych zestawów side-by-side, w których aplikacja powinna być związana w czasie wykonywania. Manifest zestawu side-by-side określa jego zależności na nazwy, wersji, zasoby i innych zestawów.  
  
 Istnieją dwa sposoby tworzenia manifestu aplikacji izolowanej lub zestawów side-by-side. Po pierwsze autor zestawu można ręcznie utworzyć plik manifestu, zgodnie z zasadami i wymaganiami w zakresie nazewnictwa. Alternatywnie Jeśli program zależy tylko zestawy języka Visual C++, takie jak CRT, MFC, ATL i inne, następnie manifestu może zostać wygenerowany automatycznie przez konsolidator.  
  
 Nagłówki bibliotek języka Visual C++ zawierają informacje o zestawie, a w przypadku bibliotek są zawarte w kodzie aplikacji, informacji o zestawie będzie używana przez konsolidator w celu utworzenia manifestu końcowym pliku binarnym. Konsolidator nie można osadzić pliku manifestu wewnątrz pliku binarnego i może generować jedynie manifestu jako zewnętrznego pliku. Posiadanie manifestu jako zewnętrznego pliku mogą nie działać w przypadku wszystkich scenariuszy. Na przykład zalecane jest, że zestawy prywatne osadzania manifestów. W kompilacji z wiersza polecenia takich jak implementacje używające nmake do kompilowania kodu można osadzić manifest za pomocą narzędzia manifestu; Aby uzyskać więcej informacji, zobacz [Generowanie manifestu w wierszu polecenia](../build/manifest-generation-at-the-command-line.md). Podczas kompilowania w programie Visual Studio, ustawiając właściwość dla narzędzia manifestu mogą być osadzone manifestu **właściwości projektu** okna dialogowego; zobacz [Manifest Generation w programie Visual Studio](../build/manifest-generation-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia związane z aplikacjami izolowanymi oraz aplikacjami zestawów Side-by-side](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)