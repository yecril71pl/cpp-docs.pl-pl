---
title: Klasy odwołania szablonu (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd720c2bdcc9bd0baab2606e473858450508feff
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107177"
---
# <a name="template-ref-classes-ccx"></a>Klasy odwołania szablonu (C + +/ CX)

Szablony C++ nie są publikowane w metadanych i dlatego nie może mieć publiczny lub chroniony ułatwień dostępu w programie. Oczywiście, używając standardowych szablonów języka C++ wewnętrznie w programach. Ponadto prywatnej klasy ref można zdefiniować jako szablonu i szablonu jawnie wyspecjalizowane klasy referencyjnej można zadeklarować jako od prywatnej składowej w klasie ref publicznego.

## <a name="authoring-ref-class-templates"></a>Tworzenie szablonów klasy ref

Poniższy przykład pokazuje sposób deklarowania prywatnej klasy ref jako szablon, a także jak deklarować standardowych szablonów języka C++ i jak je zadeklarować zarówno jako elementy członkowskie w klasie ref publicznych. Należy pamiętać, że standardowych szablonów języka C++ można wyspecjalizować przez typ środowiska wykonawczego Windows, w tym przypadku Platform::String ^.

[!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]

## <a name="see-also"></a>Zobacz też

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)