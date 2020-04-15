---
title: Korzystanie z systemu Windows z zawartymi w nich
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 5da765eae28d411c98e79af5b9173f48ea66ef8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329305"
---
# <a name="using-contained-windows"></a>Korzystanie z systemu Windows z zawartymi w nich

Atl implementuje zawarte okna z [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Zawarte okno reprezentuje okno, które deleguje swoje wiadomości do obiektu kontenera zamiast obsługi ich w swojej klasie.

> [!NOTE]
> Nie trzeba wyprowadzać klasy z `CContainedWindowT` w celu użycia okien zawartych.

Za pomocą okien zawartych można przeklasyfikować istniejącą klasę systemu Windows lub podklasę istniejącego okna. Aby utworzyć okno, które superclasses istniejącej klasy systemu Windows, najpierw `CContainedWindowT` należy określić istniejącą nazwę klasy w konstruktorze dla obiektu. Następnie `CContainedWindowT::Create`zadzwoń do . Aby podklasy istniejącego okna, nie trzeba określać nazwę klasy systemu Windows (przekazać NULL do konstruktora). Wystarczy wywołać `CContainedWindowT::SubclassWindow` metodę z dojściem do okna jest podklasy.

Zazwyczaj używane zawarte okna jako elementy członkowskie danych klasy kontenera. Kontener nie musi być oknem; jednak musi pochodzić z [CMessageMap](../atl/reference/cmessagemap-class.md).

Zawarte okno może używać alternatywnych map wiadomości do obsługi jego wiadomości. Jeśli masz więcej niż jedno okno zawarte, należy zadeklarować kilka map wiadomości alternatywnych, z których każda odpowiada oddzielnemu okno zawartemu.

## <a name="example"></a>Przykład

Poniżej przedstawiono przykład klasy kontenera z dwoma oknami zawierającymi:

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

Aby uzyskać więcej informacji na temat zawartych okien, zobacz przykład [SUBEDIT.](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)

## <a name="see-also"></a>Zobacz też

[Klasy okien](../atl/atl-window-classes.md)
