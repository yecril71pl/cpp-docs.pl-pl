---
title: Używanie okien zawartych w niej | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: f6c3b439baf05c4e4287613e9b6b5a9b1c2546b6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357924"
---
# <a name="using-contained-windows"></a>Używanie okien zawartych w niej
ATL implementuje zawartych w niej systemu windows za pomocą [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Zawartego okna reprezentuje okna, który deleguje jego komunikatów do obiektu kontenera, zamiast ich obsługę w jej własnej klasy.  
  
> [!NOTE]
>  Nie trzeba wyprowadzenia klasy z `CContainedWindowT` aby można było używać zawartych w niej systemu windows.  
  
 W systemie windows zawartych w niej można albo superklasie istniejącej klasy systemu Windows lub podklasa klasy istniejącego okna. Można utworzyć okna tego nadklas Windows istniejących klas, najpierw określ nazwę klasy istniejącego w Konstruktorze `CContainedWindowT` obiektu. Następnie wywołaj `CContainedWindowT::Create`. Do podklasy istniejącego okna, nie trzeba określić nazwę klasy systemu Windows (przekazywane **NULL** konstruktora). Po prostu Wywołaj `CContainedWindowT::SubclassWindow` metody za pomocą dojścia do okna jest podklasą klasy.  
  
 Zazwyczaj użytkownik używa okien zawartych w niej jako element członkowski danych klasy kontenera. Kontener nie musi być oknem; jednak musi pochodzić od [CMessageMap](../atl/reference/cmessagemap-class.md).  
  
 Zawartego okna można użyć mapy komunikatów alternatywnej do obsługi jego wiadomości. Jeśli masz więcej niż jedno okno zawartych w niej powinny deklarować się, że kilka alternatywny mapy komunikatów, każdy odpowiadający osobnym oknie zawartych w niej.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykładowy kontener klasy z dwóch zawartych w niej systemu windows:  
  
 [!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]  
  
 Aby uzyskać więcej informacji na temat zawartych w niej systemu windows, temacie [SUBEDIT](../visual-cpp-samples.md) próbki.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy okien](../atl/atl-window-classes.md)

