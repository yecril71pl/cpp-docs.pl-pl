---
title: "składnik | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.component
- component_CPP
dev_langs:
- C++
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3edb2f68b479eeadca777e0707dd96e148d13fe8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="component"></a>składnik
Kontroluje zbieranie informacji dotyczących przeglądania lub informacji zależności z plików źródłowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      #pragma component( browser, { on | off }[, references [, name ]] )  
#pragma component( minrebuild, on | off )  
#pragma component( mintypeinfo, on | off )  
```  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="browser"></a>Przeglądarka  
 Można włączyć lub wyłączyć zbieranie, a także określić szczególne nazwy do zignorowania podczas zbierania informacji.  
  
 Używanie włączania/wyłączania kontroli kolekcji informacji dotyczących przeglądania z pragmy do przodu. Na przykład:  
  
```  
#pragma component(browser, off)  
```  
  
 zatrzymuje kompilator zbierający informacje dotyczące przeglądania.  
  
> [!NOTE]
>  Aby włączyć zbieranie informacji o przeglądaniu z tej pragmy [informacje o przeglądaniu, należy najpierw włączyć](../build/reference/building-browse-information-files-overview.md).  
  
 **Odwołania** opcja może być używana z lub bez *nazwa* argumentu. Przy użyciu **odwołania** bez *nazwa* Włącza lub wyłącza zbieranie odwołań (inne informacje o przeglądaniu w dalszym ciągu będą zbierane, jednak). Na przykład:  
  
```  
#pragma component(browser, off, references)  
```  
  
 zatrzymuje kompilator zbierający informacje dotyczących odwołań.  
  
 Przy użyciu **odwołania** z *nazwa* i **poza** uniemożliwia odwołania do *nazwa* były wyświetlane w oknie informacje przeglądania. Użyj następującej składni, aby zignorować nazwy i typy, którymi nie jesteś zainteresowany i zmniejsz rozmiar plików przeglądania informacji. Na przykład:  
  
```  
#pragma component(browser, off, references, DWORD)  
```  
  
 ignoruje odwołania do **DWORD** od tej pory. Można włączyć zbieranie odwołań do `DWORD` kopii na za pomocą **na**:  
  
```  
#pragma component(browser, on, references, DWORD)  
```  
  
 To jest jedynym sposobem, aby kontynuować zbieranie odwołań do *nazwa*; trzeba jawnie włączyć na każdym *nazwa* który zostało wyłączone.  
  
 Aby zapobiec preprocesora rozszerzanie *nazwa* (takich jak rozszerzanie **NULL** do **0**), umieść go w cudzysłowy:  
  
```  
#pragma component(browser, off, references, "NULL")  
```  
  
## <a name="minimal-rebuild"></a>Minimalna ponowna kompilacja  
 Funkcja minimalnej kompilacji ponownej Visual C++ wymaga, aby kompilator tworzył i przechowywał informacje zależności klasy języka C++, które zajmują miejsce na dysku. Aby zaoszczędzić miejsce na dysku, można użyć `#pragma component( minrebuild, off )` zawsze, gdy nie ma potrzeby zbierania informacji o zależnościach, na przykład niezmiennych pliki nagłówków. Wstaw `#pragma component(minrebuild, on)` po niezmiennych klas, aby włączyć zależność kolekcji kopii na.  
  
## <a name="reduce-type-information"></a>Ograniczenie informacji typu  
 **Mintypeinfo** opcja zmniejsza informacji o debugowaniu dla określonego regionu. Wielkość tych informacji jest znaczna i dotyczy plików .pdb i .obj. Nie można debugować klas i struktur w regionie mintypeinfo. Korzystanie z opcji mintypeinfo może być pomocne, aby uniknąć następującego ostrzeżenia:  
  
```  
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information  
```  
  
 Aby uzyskać więcej informacji, zobacz [włączyć minimalnego odbudować](../build/reference/gm-enable-minimal-rebuild.md) (/ Gm) — opcja kompilatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)