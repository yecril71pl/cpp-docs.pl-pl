---
title: "-DW (Wyłącz przemieszczanie konstrukcji) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /vd
dev_langs: C++
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b945c4a3191554d5299522ff376772d6362a616c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="vd-disable-construction-displacements"></a>/vd (Wyłącz przemieszczanie konstrukcji)
## <a name="syntax"></a>Składnia  
  
```  
/vdn  
```  
  
## <a name="arguments"></a>Argumenty  
 `0`  
 Pomija Członkowskie przemieszczanie konstruktora/destruktora vtordisp. Wybierz tę opcję tylko wtedy, gdy masz pewność, wszystkie klasy konstruktory i destruktory wywołać wirtualnego działa praktycznie.  
  
 `1`  
 Umożliwia tworzenie elementów członkowskich przemieszczanie konstruktora/destruktora vtordisp ukryte. Ten wybór jest ustawieniem domyślnym.  
  
 `2`  
 Umożliwia użycie [dynamic_cast Operator](../../cpp/dynamic-cast-operator.md) obiektu tworzona. Na przykład dynamic_cast z wirtualnej klasy podstawowej w klasie pochodnej.  
  
 **/ vd2** dodaje pole vtordisp, jeśli masz wirtualnej podstawy z funkcji wirtualnych. **/ vd1** powinno wystarczyć. Najbardziej typowe przypadek where **/vd2** jest niezbędne jest, gdy destruktora jest funkcją wirtualną tylko w podstawowym wirtualnego.  
  
## <a name="remarks"></a>Uwagi  
 Opcje te dotyczą tylko kod w języku C++, która korzysta z wirtualnymi podstawami.  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]implementuje obsługi przemieszczanie konstrukcji języka C++ w sytuacjach, w których jest używany wirtualnego dziedziczenia. Przemieszczanie konstrukcji rozwiązuje problem utworzenia funkcją wirtualną zadeklarowanej w wirtualnej podstawy i przesłonięcia w klasie pochodnej, jest wywoływana z konstruktora podczas konstruowania dalsze klasy pochodnej.  
  
 Problem jest, że funkcji wirtualnej mogą być przekazywane przez niepoprawny `this` wskaźnika w związku z tym rozbieżności między przemieszczanie do wirtualnej podstaw klasę i przemieszczanie do jej klas pochodnych. Rozwiązanie zawiera dostosowania przemieszczenie pojedynczego konstrukcji, nazywane polem vtordisp dla każdej wirtualnej podstawy klasy.  
  
 Domyślnie vtordisp — pola są wprowadzane za każdym razem kod definiuje użytkownika konstruktory i destruktory i zastępuje również funkcji wirtualnych z wirtualnymi typami podstawowymi.  
  
 Te opcje wpływa na całą źródłową plików. Użyj [vtordisp](../../preprocessor/vtordisp.md) do pomijania, a następnie ponownie włącz vtordisp — pola na podstawie klasy klasy.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)