---
title: Za pomocą ograniczonego Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc17925e36e0e224a657177d0aa18912c564efed
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850803"
---
# <a name="using-contained-windows"></a>Za pomocą ograniczonego Windows
ATL implementuje okien zawartych z [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Zawartego okna reprezentuje okna, który deleguje swoje wiadomości do obiektu kontenera, zamiast ich obsługę w jej własnej klasy.  
  
> [!NOTE]
>  Nie należy wyprowadzić klasę z `CContainedWindowT` aby można było używać okien zawartych.  
  
 Za pomocą okien zawartych można albo superklasie istniejącej klasy Windows lub podklasy istniejącego okna. Można utworzyć okna tego superklas Windows istniejącej klasy, należy najpierw określić istniejącą nazwę klasy w Konstruktorze `CContainedWindowT` obiektu. Następnie wywołaj `CContainedWindowT::Create`. Do podklasy istniejącego okna nie trzeba określić nazwę klasy Windows (— dostęp próbny o wartości NULL do konstruktora). Po prostu Wywołaj `CContainedWindowT::SubclassWindow` metody za pomocą dojścia do okna, jest podklasą klasy.  
  
 Zazwyczaj używa się okien zawartych jako elementy członkowskie danych klasy kontenera. Kontener musi być okna; jednak musi pochodzić od [CMessageMap](../atl/reference/cmessagemap-class.md).  
  
 Zawartego okna mogą używać mapy komunikatów alternatywnej do obsługi swojej wiadomości. Jeśli masz więcej niż jeden zawartego okna, powinny deklarować, że kilka alternatywny mapy komunikatów, każdej odpowiadającej oddzielne okno zawarte.  
  
## <a name="example"></a>Przykład  
 Oto przykład klasy kontenera za pomocą dwóch okien zawartych:  
  
 [!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]  
  
 Aby uzyskać więcej informacji na temat okien zawartych zobacz [SUBEDIT](../visual-cpp-samples.md) próbki.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy okien](../atl/atl-window-classes.md)

