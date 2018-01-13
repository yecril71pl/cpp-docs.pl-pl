---
title: ATL okna cech | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fda95e4517d2717a89310a8e49a0c5b337feebcf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-window-traits"></a>Opis cech okna
Klasy okien cech Podaj prostą metodę standaryzacji stylów używany do tworzenia obiektu ATL okna. Okno cechy są akceptowane jako parametry szablonu przez [CWindowImpl](../atl/reference/cwindowimpl-class.md) i innych klas okien ALT sposób zapewnienia domyślne style okna na poziomie klasy.  
  
 Jeśli twórca wystąpienia okna nie udostępnia style jawnie w wywołaniu [Utwórz](../atl/reference/cwindowimpl-class.md#create), klasa cech umożliwia Sprawdź, czy okno jest nadal utworzone przy użyciu stylów poprawne. Można nawet zagwarantować, że niektóre style są ustawione dla wszystkich wystąpień tej klasy okna umożliwiając inne style można konfigurować na poszczególnych wystąpień.  
  
## <a name="atl-window-traits-templates"></a>Szablony cech okna ATL  
 ATL zapewnia dwóch szablonów cech okna, które umożliwiają skonfigurowanie domyślnych stylów w czasie kompilacji przy użyciu ich parametrów szablonu.  
  
|Class|Opis|  
|-----------|-----------------|  
|[CWinTraits](../atl/reference/cwintraits-class.md)|Użyj tego szablonu, gdy chcesz zapewnić domyślne style okna, które będą używane tylko wtedy, gdy nie inne style są określone w wywołaniu **Utwórz**. Style udostępniane w czasie wykonywania mają pierwszeństwo przed za pośrednictwem style na czas kompilacji.|  
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|Użyj tej klasy, jeśli chcesz określić style, które muszą być zawsze ustawiony dla klasy okna. Style udostępniane w czasie wykonywania są łączone z style ustawienie w czasie kompilacji przy użyciu bitowego operatora OR.|  
  
 Oprócz tych szablonów, ATL zawiera szereg wstępnie zdefiniowanych specjalizacjach `CWinTraits` szablonu dla często używanych kombinacji Style okna. Zobacz [CWinTraits](../atl/reference/cwintraits-class.md) odwołania dokumentacji, aby uzyskać szczegółowe informacje.  
  
## <a name="custom-window-traits"></a>Cechy niestandardowych okien  
 W sytuacji mało prawdopodobne, co specjalizujących szablonów podał ATL nie jest wystarczające i należy utworzyć własny klasa cech, wystarczy utworzyć klasę, która implementuje dwie funkcje statyczne: `GetWndStyle` i **GetWndStyleEx** :  
  
 [!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]  
  
 Każda z tych funkcji zostaną przekazane jedna z wartości stylu w czasie wykonywania, którego można użyć do utworzenia nowej wartości stylu. Jeśli okno cech klasy jest używany jako argument szablonu klasy okna ATL, wartości stylu przekazany do funkcji statycznych będzie niezależnie od został przekazany jako argument stylu [Utwórz](../atl/reference/cwindowimpl-class.md#create).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy okien](../atl/atl-window-classes.md)

