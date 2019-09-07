---
title: Klasy ref szablonu (C++/CX)
ms.date: 01/22/2017
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
ms.openlocfilehash: 3e9c233b5227b4ad86eb632db740001bc2a3a8bd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740852"
---
# <a name="template-ref-classes-ccx"></a>Klasy ref szablonu (C++/CX)

C++szablony nie są publikowane w metadanych i dlatego nie mogą mieć publicznej ani chronionej dostępności w programie. Można oczywiście używać standardowych C++ szablonów wewnętrznie w programie. Ponadto można zdefiniować prywatną klasę ref jako szablon i można zadeklarować jawnie wyspecjalizowaną klasę ref szablonu jako prywatną składową w publicznej klasie referencyjnej.

## <a name="authoring-ref-class-templates"></a>Tworzenie szablonów klas referencyjnych

Poniższy przykład pokazuje sposób deklarowania prywatnej klasy ref jako szablonu, a także sposobu deklarowania standardowego C++ szablonu i sposobu deklarowania ich jako elementów członkowskich w publicznej klasie referencyjnej. Należy pamiętać, że C++ standardowy szablon może być wyspecjalizowany dla typu środowisko wykonawcze systemu Windows, w tym przypadku platform:: String ^.

[!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]

## <a name="see-also"></a>Zobacz także

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
