---
title: "Ostrzeżenie LNK4105 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4105
dev_langs: C++
helpviewer_keywords: LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d64ff3756f709820c7e25b2986b8529a364139e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4105"></a>Ostrzeżenie LNK4105 narzędzi konsolidatora
Brak argumentu określona z opcją "option"; Ignorowanie opcji  
  
 To ostrzeżenie występuje tylko gdy [/libpath](../../build/reference/libpath-additional-libpath.md) opcja jest ustawiona. Jeśli nie określono katalogu przy użyciu tej opcji, konsolidator ignoruje opcję i generuje ten komunikat ostrzegawczy.  
  
 Jeśli musisz zastąpić istniejące ustawienia środowiska biblioteki, Usuń opcję/libpath z wiersza polecenia konsolidatora. Jeśli chcesz użyć ścieżki alternatywnej wyszukiwania dla bibliotek, określ ścieżkę alternatywną, zgodnie z opcją/libpath.  
  
## <a name="example"></a>Przykład  
  
```  
link /libpath:c:\filepath\lib bar.obj  
```  
  
 czy bezpośrednie konsolidator, aby wyszukać wymaganych bibliotek w `c:\filepath\lib` przed wyszukiwaniem w lokalizacji domyślnej.