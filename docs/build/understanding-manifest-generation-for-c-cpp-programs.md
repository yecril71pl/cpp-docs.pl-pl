---
title: "Opis Generowanie manifestu dla programów C/C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5b0d17ba04dc1648d9aa05dff98715ef9a80a230
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Ogólne informacje o tworzeniu manifestu dla programów C/C++
A [manifestu](http://msdn.microsoft.com/library/aa375365) dokument XML, który może być plik XML lub zasobu osadzonego w aplikacji lub zestawu. Manifest [izolowany aplikacji](http://msdn.microsoft.com/library/aa375190) służy do zarządzania nazwy i wersje udostępnionych zestawów side-by-side, do których aplikacji muszą być powiązane w czasie wykonywania. Manifest zestawu side-by-side określa zależnościami na nazwy, wersji, zasobów i innych zestawów.  
  
 Istnieją dwa sposoby tworzenia manifestu izolowanych aplikacji lub zestawu side-by-side. Po pierwsze autorem zestawu można ręcznie utworzyć plik manifestu reguły i wymagania nazewnictwa. Alternatywnie Jeśli program zależy tylko zestawy Visual C++, takie jak CRT, MFC, ATL lub innych, następnie manifestu może zostać wygenerowany automatycznie przez konsolidator.  
  
 Nagłówki bibliotek języka Visual C++ zawierają informacje o zestawie, i gdy biblioteki zostaną uwzględnione w kodzie aplikacji, informacje o tym zestawie jest używany przez konsolidator do utworzenia manifeście końcowym danych binarnych. Konsolidator nie można osadzić pliku manifestu w danych binarnych, a można generować tylko jako zewnętrzny plik manifestu. Posiadanie jako zewnętrzny plik manifestu mogą nie działać w przypadku wszystkich scenariuszy. Na przykład zaleca się, że zestawy prywatne osadzania manifestów. W kompilacjach wiersza polecenia, takich jak implementacje używające nmake do kompilacji kodu umożliwia osadzanie manifestu za pomocą narzędzia manifestu; Aby uzyskać więcej informacji, zobacz [Generowanie manifestu w wierszu polecenia](../build/manifest-generation-at-the-command-line.md). Podczas kompilowania [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], można ją osadzić manifestu przez ustawienie właściwości dla narzędzia manifestu w **właściwości projektu** okna dialogowego; zobacz [Generowanie manifestu w Visual Studio](../build/manifest-generation-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje izolowane i zestawy Side-by-side](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Tworzenie C/C++ izolowane Side-by-side zestawów ani aplikacji](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)